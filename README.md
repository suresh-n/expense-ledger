# The Ledger — Setup Guide

## 1. Put this on GitHub Pages
1. Create a new GitHub repo (e.g. `expense-ledger`).
2. Upload `index.html` to the repo root (must be named exactly `index.html` for Pages to serve it at the root URL).
3. Go to **Settings → Pages** in the repo.
4. Under "Build and deployment", set **Source: Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
5. GitHub gives you a URL like `https://<your-username>.github.io/expense-ledger/` within a minute or two — that's your app, open it on any device.

## 2. Set up the Google Sheet + Apps Script backend
1. Go to [sheets.google.com](https://sheets.google.com) and create a new blank Sheet. Name it whatever you like (e.g. "Ledger Data").
2. In the Sheet, go to **Extensions → Apps Script**.
3. Delete any starter code in `Code.gs` and paste in the contents of `Code.gs` from this folder.
4. Click **Deploy → New deployment**.
5. Click the gear icon next to "Select type" → choose **Web app**.
6. Set:
   - **Execute as:** Me
   - **Who has access:** Anyone
7. Click **Deploy**. Authorize the permissions it asks for (it needs to read/write the Sheet).
8. Copy the **Web app URL** it gives you (looks like `https://script.google.com/macros/s/AKfycb.../exec`).

## 3. Connect the app to the Sheet
1. Open your GitHub Pages URL.
2. Go to the **Settings** tab inside the app.
3. Paste the Web app URL into the "Apps Script Web App URL" field, click **Save URL**.
4. Add a test entry from the **Entry** tab, then check the **Ledger** tab shows it, and open the Sheet directly to confirm the row landed there too.

## Notes
- The Sheet is the single source of truth. The Ledger and Dashboard tabs always pull fresh data from it, so laptop and mobile both show the same picture.
- If you ever change the Apps Script code, redeploy via **Deploy → Manage deployments → Edit (pencil icon) → New version → Deploy** — this keeps the same URL rather than generating a new one.
- The Sheet URL is stored only in each browser's local storage — you'll need to paste it in once per browser/device.
