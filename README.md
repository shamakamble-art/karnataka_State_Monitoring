[README.md](https://github.com/user-attachments/files/32100591/README.md)
# Publishing the Karnataka monitoring map

This folder is the whole website. It is one file — `index.html`. Put it on any web host
and you get a link you can share with the team.

## Why it has to be hosted

Opening `index.html` by double-clicking it works, but the live connection to the sheet will
usually fail. Browsers treat a file opened from your computer as an untrusted origin and block
it from calling Google. Once the same file is served from a web address, the block goes away
and the map reads the sheet on every load.

## Option 1 — GitHub Pages (recommended, free, ~5 minutes)

1. Go to https://github.com/new and create a repository. Name it something like
   `karnataka-monitoring-map`. Set it to **Public**. Click *Create repository*.
2. On the new repo page, click **uploading an existing file**.
3. Drag `index.html` into the box and click **Commit changes**.
4. Go to **Settings → Pages**.
5. Under *Build and deployment*, set **Source** to `Deploy from a branch`,
   **Branch** to `main` and folder to `/ (root)`. Click **Save**.
6. Wait 1–2 minutes, then refresh the Settings → Pages screen. Your link appears at the top:

   `https://<your-username>.github.io/karnataka-monitoring-map/`

That is the link to share. To update the map later, upload a new `index.html` over the old one.

## Option 2 — Netlify Drop (fastest, no account needed to try)

1. Go to https://app.netlify.com/drop
2. Drag this **whole folder** onto the page.
3. You get a live link in about ten seconds.

Sign in afterwards if you want to keep the link permanently and give it a nicer name.

## Check it worked

Open your new link. The status bar at the top of the page should turn **green** and say
which route it used and what time it read the sheet. Change a cell in the sheet, wait a
minute (or press *Refresh now*) and the map should follow.

## If the status bar is still red

The page tries three ways to read the sheet before giving up. If all three fail, open
**"Sheet won't load? Two ways to fix it"** at the bottom of the page and use a published link:

1. In the sheet: **File → Share → Publish to web**
2. Pick the sheet tab, choose **Comma-separated values (.csv)**, click **Publish**
3. Copy the link it gives you
4. Paste it into the box on the map page and click **Use this link**

To make that permanent for everyone, add it to the end of your shared URL:

`https://<your-link>/?csv=<the-published-csv-link>`

## What the page reads

It matches columns by the words in the header row, not by position, so you can add, move or
rename columns and it keeps working. It looks for headers containing: *district*, *division*,
*POC*, *calendar*, *CRP workshop*, *DIET*, *BRP*, *CRP interview*, *morning assembly*, and
*school visit*. All the morning-assembly and school-visit columns are picked up automatically,
however many there are.

Checkbox columns are read correctly — `FALSE` counts as not done. Text columns count as done
for anything except blank, `no`, `pending`, `not done`, `NA`, `0` or `-`.

The page only ever reads. It cannot change anything in the sheet.
