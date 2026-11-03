# Jacob & Sejin: wedding invitation (v6)

A single-page animated invitation: the envelope opens, then the watercolour scenes scroll by with a gentle 2.5D depth effect, and guests RSVP straight into a Google Sheet.

## What's in the folder

| File | What it is |
|---|---|
| `index.html` | The invitation |
| `art/` | The paintings and florals (about 1.2 MB in total) |
| `preview.jpg` | The picture shown when the link is sent by text, WhatsApp and so on |
| `wedding.ics` | "Add to calendar" file with both events |
| `apps-script.gs` | The small script that writes RSVPs into the Google Sheet |

## 1. Put it on GitHub Pages

1. Create a public repository called **jacob-and-sejin** under the `peanutalloy-a11y` account.
2. Upload everything in this folder (not the folder itself) to the repository root.
3. Go to **Settings → Pages**, set Source to "Deploy from a branch", pick `main` and `/ (root)`, then save.
4. After a minute or two the invitation is live at
   `https://peanutalloy-a11y.github.io/jacob-and-sejin/`

If you use a different repository name, change the two addresses near the top of `index.html` (`og:url` and `og:image`) so the link preview still shows the picture.

## 2. Connect the RSVP form to the Google Sheet

1. Open the sheet **Jacob & Sejin – Wedding RSVPs** in Google Drive.
2. **Extensions → Apps Script**, delete what's there, paste in `apps-script.gs`, and save.
3. **Deploy → New deployment → Web app**. Execute as **Me**, access **Anyone**. Deploy and allow the permissions.
4. Copy the web app address (it ends in `/exec`).
5. In `index.html`, find `sheetUrl: ''` and paste the address between the quotes. Commit the change.

Until `sheetUrl` is filled in, the form falls back to opening an email to `RSVP.email` (and a text, if you add a mobile number to `RSVP.phone`).

## How the depth effect works

Each scene has two planes:

1. The full painting, which drifts slowly as you scroll.
2. A transparent floral spray in front, which moves a little faster.

There is no cut-out middle layer, so there are no smears or ghost edges. People who have "reduce motion" turned on see everything still.

## Changes from v5

- Full paintings are back as the scene layer, and the cut-out architecture and blurred "distant" plates are removed.
- The Google Sheets RSVP is restored, with a thank-you message and spam protection.
- The second daytime harbour under the names has been replaced with the balustrade. The sunset harbour now closes the invitation.
- Sections no longer overlap, so the ceremony map link and arrows can be tapped.
- Foreground florals have been moved off the bridge, spire and pier.
- Images went from 4.5 MB to about 1.2 MB, and duplicate and unused files were removed.
- The link preview uses full addresses.
- The calendar file uses UTC times and standard line endings.
- The envelope waits for the card to finish rising before fading.
- All images reserve their space, so nothing jumps while loading.

## Before sending

- Check the RSVP email address in `index.html` (`RSVP.email`).
- Send yourself the link by text to check the preview, then submit a test RSVP and delete that row from the sheet.
