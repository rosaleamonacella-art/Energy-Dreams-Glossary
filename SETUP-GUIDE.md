# Energy Dreams Glossary — Setup Guide

## Overview

This guide walks you through three steps:
1. **Create a Google Form + Google Sheet** (students submit entries here)
2. **Publish the Google Sheet as CSV** (the website reads data from here)
3. **Deploy to GitHub Pages** (makes the site live)

Total setup time: ~30 minutes.

---

## STEP 1: Create the Google Form + Sheet

### 1a. Create the Google Sheet

1. Go to [Google Sheets](https://sheets.google.com) and create a new spreadsheet
2. Name it **"Energy Dreams Glossary"**
3. In **Row 1**, create these exact column headers (spelling matters):

| A | B | C | D | E | F | G | H | I |
|---|---|---|---|---|---|---|---|---|
| **Term** | **Definition** | **Tags** | **Cross-References** | **Citations** | **Author** | **Date** | **Image URL** | **Media URL** |

4. Leave the sheet otherwise empty — student entries will populate it

### 1b. Create the Google Form

1. Go to [Google Forms](https://forms.google.com) and create a new form
2. Name it **"Energy Dreams — Submit Glossary Entry"**
3. Add a description: *"Submit a new term to the Energy Dreams collaborative glossary."*
4. Create the following fields **in this exact order**:

| # | Field Name | Field Type | Required? | Help Text |
|---|-----------|-----------|-----------|-----------|
| 1 | **Term** | Short answer | ✅ Yes | *The term or concept you are defining* |
| 2 | **Definition** | Paragraph | ✅ Yes | *Your definition (2–5 sentences recommended)* |
| 3 | **Tags** | Short answer | ✅ Yes | *Comma-separated tags, e.g.: energy, geology, colonialism, labor* |
| 4 | **Cross-References** | Short answer | No | *Other glossary terms this relates to, comma-separated, e.g.: Extraction, Fossil Capital* |
| 5 | **Citations** | Paragraph | No | *Separate multiple citations with a semicolon (;)* |
| 6 | **Author** | Short answer | ✅ Yes | *Your name* |
| 7 | **Date** | Date | ✅ Yes | *Today's date* |
| 8 | **Image URL** | Short answer | No | *Optional: URL to an image (use Google Drive sharing link or Imgur)* |
| 9 | **Media URL** | Short answer | No | *Optional: link to video, reading, or other media* |

### 1c. Link the Form to the Sheet

1. In Google Forms, click the **Responses** tab
2. Click the green Sheets icon (📊) → **"Select existing spreadsheet"**
3. Choose your **"Energy Dreams Glossary"** sheet
4. Google will create a new tab called **"Form Responses 1"**

### 1d. Fix the column headers

When the form links to the sheet, it creates its own headers. You need to **rename them** to match what the website expects:

1. Go to the **"Form Responses 1"** tab in your sheet
2. You'll see a "Timestamp" column first — **delete the entire Timestamp column** (right-click column A → Delete column)
3. Rename the remaining headers to match exactly:
   - `Term`
   - `Definition`
   - `Tags`
   - `Cross-References`
   - `Citations`
   - `Author`
   - `Date`
   - `Image URL`
   - `Media URL`

> **Important:** The column headers must match these names exactly (case-sensitive).

---

## STEP 2: Publish the Google Sheet as CSV

1. In your Google Sheet, go to **File → Share → Publish to web**
2. In the dropdown, select the **"Form Responses 1"** tab (not "Entire Document")
3. Change the format from "Web page" to **"Comma-separated values (.csv)"**
4. Click **Publish**
5. **Copy the URL** it gives you — it will look something like:
   ```
   https://docs.google.com/spreadsheets/d/e/2PACX-1vS.../pub?gid=123456&single=true&output=csv
   ```
6. Save this URL — you'll need it in Step 3

> **Note:** The sheet auto-updates. When a student submits via the form, the CSV updates within a few minutes, and the website will show the new entry on the next page load.

---

## STEP 3: Deploy to GitHub Pages

### 3a. Create a GitHub repository

1. Go to [GitHub](https://github.com) and sign in (or create an account)
2. Click the **+** button → **New repository**
3. Name it: `energy-dreams-glossary`
4. Set it to **Public**
5. Check **"Add a README file"**
6. Click **Create repository**

### 3b. Upload the index.html file

1. In your new repository, click **"Add file"** → **"Upload files"**
2. Upload the `index.html` file from the deployment package
3. Click **"Commit changes"**

### 3c. Configure the two URLs

1. In your repository, click on `index.html` to open it
2. Click the **pencil icon** (✏️) to edit
3. Find these two lines near the top of the `<script>` section:

   ```javascript
   const GOOGLE_SHEET_CSV_URL = "YOUR_PUBLISHED_CSV_URL_HERE";
   const GOOGLE_FORM_URL = "YOUR_GOOGLE_FORM_URL_HERE";
   ```

4. Replace `YOUR_PUBLISHED_CSV_URL_HERE` with the CSV URL from Step 2
5. Replace `YOUR_GOOGLE_FORM_URL_HERE` with the sharing URL of your Google Form:
   - In Google Forms, click **Send** → copy the link (or use the shortened URL)
6. Click **"Commit changes"**

### 3d. Enable GitHub Pages

1. In your repository, go to **Settings** → **Pages** (in the left sidebar)
2. Under "Source", select **"Deploy from a branch"**
3. Set the branch to **main** and folder to **/ (root)**
4. Click **Save**
5. Wait 1–2 minutes, then refresh the page
6. You'll see a URL like: `https://yourusername.github.io/energy-dreams-glossary/`

**That's your live glossary!** 🎉

---

## How It Works

```
Student fills out Google Form
        ↓
Response saved to Google Sheet
        ↓
Sheet auto-published as CSV
        ↓
Website fetches CSV on each page load
        ↓
Entry appears on the glossary
```

- **No approval step** — entries go live automatically (you can edit/delete rows in the Google Sheet at any time)
- **To remove an entry** — delete the row from the Google Sheet
- **To edit an entry** — edit the cell directly in the Google Sheet
- **Refresh delay** — Google's published CSV can take 1–5 minutes to update after a new submission

---

## Column Format Reference

For students, here's how each field should be formatted:

| Field | Format | Example |
|-------|--------|---------|
| **Term** | Single term or concept | `Sacrifice Zone` |
| **Definition** | 2–5 sentences | `A geographic area permanently impaired by...` |
| **Tags** | Comma-separated, lowercase | `energy, environmental justice, landscape` |
| **Cross-References** | Comma-separated, exact term names | `Extraction, Slow Violence` |
| **Citations** | Semicolon-separated | `Nixon 2011; Klein 2014` |
| **Author** | Your name | `Jane Smith` |
| **Date** | YYYY-MM-DD | `2026-02-15` |
| **Image URL** | Full URL (optional) | `https://drive.google.com/...` |
| **Media URL** | Full URL (optional) | `https://youtube.com/...` |

---

## Troubleshooting

**Entries not appearing?**
- Check that the Google Sheet is published (File → Share → Publish to web)
- Ensure column headers match exactly: `Term`, `Definition`, `Tags`, `Cross-References`, `Citations`, `Author`, `Date`, `Image URL`, `Media URL`
- Allow up to 5 minutes for Google to update the published CSV
- Open the CSV URL directly in a browser to check it's working

**Network view is empty?**
- You need at least 2 entries with cross-references to each other for connections to appear
- Entries sharing 2+ tags will also show dotted connections

**Want a custom domain?**
- In GitHub Pages settings, you can add a custom domain (e.g., `energydreams.gsd.harvard.edu`)
- Ask GSD IT to create a CNAME record pointing to `yourusername.github.io`

---

## Sharing with Students

Send students:
1. The **Google Form link** to submit entries
2. The **live site URL** to browse the glossary
3. The column format reference above so they know how to format tags, cross-references, and citations
