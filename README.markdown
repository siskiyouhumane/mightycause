# Mightycause - North State Giving Tuesday

This repo is home for code used by the Siskiyou Humane Society to develop
their campaign pages for northstategives.org, which currently runs on the
Mightycause platform. Feel free to reuse this code. Pull requests for
relevant fixes from the public are welcome.

## Previewing a page before you publish

Mightycause has no draft or staging mode: anything saved in the page editor
is live immediately. `LOAD-ME-IN-BROWSER.html` lets you see what a page will
look like first, using the real northstategives.org stylesheets and layout.

A Mightycause page has two kinds of content:

* **Page settings** — banner image, logo, organization name, theme color,
  banner filter, goal, and the optional custom tab. These are set in the
  page's settings on Mightycause, and images are uploaded there.
* **The story** — the HTML you edit with the `<>` code view button in the
  editor. That is what `organization_page.html` holds.

The preview handles both.

### For everyone (no tools needed)

1. Double-click `LOAD-ME-IN-BROWSER.html` to open it in your browser.
2. **Story:** paste your HTML into the text box, or click **Open HTML file…**
   and pick a saved `.html` file (for example `organization_page.html`).
   The preview updates as you type.
3. **Banner, logo, name, colors, goal:** change them under **Page settings**
   at the top of the panel. Upload a banner or logo to see how it will look;
   the preview crops it exactly as Mightycause does (banner 3:1, logo 1:1),
   so you can tell what will be cut off before you upload for real.
   **Reset to live page** puts back what is on the live page now.
4. Switch between **Desktop / Tablet / Phone**. Most Giving Tuesday visitors
   are on phones, so check that view before you call it done.
5. Read the warnings under the text box. Orange ones are things the
   Mightycause editor will delete when you paste; blue ones are suggestions.
6. When it looks right: click **Copy HTML**, open your page on
   northstategives.org, click `<>` in the editor, replace everything with
   what you copied, and save. Then upload the banner and logo in the page
   settings and set the name, colors and goal to match.

Everything you change is remembered in the browser, so you can close the
tab and come back to it later. Uploaded images are kept only in that
browser — keep the original files somewhere safe too.

### For developers

Serve the folder and pass the story file name in the URL so it reloads
from disk:

    python3 -m http.server 8000
    # then open http://localhost:8000/LOAD-ME-IN-BROWSER.html?file=organization_page.html

Keep each page's HTML in its own file in this repo and commit before and
after every change to the live page; that is the backup Mightycause doesn't
give you. Banner and logo originals belong in the repo too.

### What the preview can't do

The Mightycause editor (Froala) runs its own cleanup when you paste. The
preview flags the common cases — `<script>`, `<style>`, `<iframe>`, form
elements, event handlers, custom `class` names — but it is not the same
code. After saving a page, look at it once on the live site. To experiment
with what survives the editor, create a personal campaign page, set it to
hidden, and use that as a sandbox rather than the organization page.

The header, buttons, goal bar and tabs are redrawn from the live page's
own CSS rules (captured 2026-10-29); the "Matched!" sticker, Giving
Activity, gallery and Organization Data sections are placeholders. The
stylesheet list in `LOAD-ME-IN-BROWSER.html` was captured the same day. If
Mightycause renames `styles-XXXX.css` the preview falls back to built-in
approximations (same font, sizes and colours); it will still be close.
