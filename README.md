# fallnote

> The Notion killer. Sovereign single-HTML block-based note + database substrate.

**Live:** https://sjgant80-hub.github.io/fallnote/
**Estate:** https://www.ai-nativesolutions.com

## What it kills

Notion. Roam. Coda. Obsidian (partially — fallnote is online-first by design).

What you get:
- **Block-based editor** — paragraph · h1/h2/h3 · bullet · numbered · todo · quote · callout · code · divider · link-to-page
- **Nested pages** — page-inside-page tree, infinite depth
- **Databases with table view** — title · text · number · date · select · multi-select · checkbox properties
- **Slash menu** (`/`) — turn any block into any type
- **Wiki links** (`[[`) — autocomplete + backlinks
- **Markdown shortcuts** — `**bold**` · `*italic*` · `` `code` `` · `~~strike~~`
- **Global search** — across all pages and blocks
- **Export** — page → markdown, workspace → JSON
- **Import** — markdown files, JSON, Notion JSON export

## What it doesn't have (yet — v2)

- Board / calendar / gallery / timeline views (table only in v1)
- Formula · rollup · relation properties
- Image uploads (use external URLs for now)
- Templates
- Real-time multi-user collab
- Cloudflare KV cross-device sync (v2)

## Sovereignty contract

- **Your data lives in your browser's IndexedDB.** Never sent anywhere.
- **No analytics. No tracking. No telemetry.** Open DevTools → Network — nothing leaves your machine.
- **not subscription-based. No login. No account.** Open the page, you have it.
- **MIT-licensed.** Fork it. Modify it. Sell your fork. Whatever.
- **One file.** ~50KB gzipped. Save the HTML to disk and it runs offline forever.
- **If I disappear**, the file you saved keeps working.

## Install

### Option 1 — use the hosted page (easiest)
Bookmark https://sjgant80-hub.github.io/fallnote/ · install as PWA from your browser menu · done.

### Option 2 — save the file (most sovereign)
1. Right-click https://sjgant80-hub.github.io/fallnote/ → Save Page As → `fallnote.html`
2. Double-click `fallnote.html` whenever you want it.
3. Your IndexedDB is per-origin so the saved file gets its own storage.

### Option 3 — fork it
1. Fork the repo on GitHub
2. Edit `index.html` to suit
3. Enable GitHub Pages on the fork → you have your own deployment

## Keyboard shortcuts

| Key | Action |
|---|---|
| `/` | Open slash menu (change block type) |
| `[[` | Open wiki-link autocomplete |
| `Enter` | New block (same type) |
| `Shift + Enter` | Line break within block |
| `Tab` | Indent block |
| `Shift + Tab` | Outdent block |
| `Backspace` at start | Merge with previous block |
| `Cmd/Ctrl + K` | Open command palette |
| `Cmd/Ctrl + P` | Quick-jump to page |
| `Cmd/Ctrl + S` | Force-save (auto-saves anyway) |
| `**text**` | Bold |
| `*text*` | Italic |
| `` `text` `` | Inline code |
| `~~text~~` | Strikethrough |

## Architecture

- **One HTML file.** All UI, logic, CSS, data inside.
- **IndexedDB** named `fallnote_db` stores `pages` + `blocks` + `meta`.
- **No dependencies.** Vanilla JS. No frameworks. No build step.
- **Block model:** every block has `{id, page_id, parent_block_id, type, content, position}`. Same recursion for headings, lists, todos, callouts.
- **Page model:** every page has `{id, parent_page_id, title, icon, is_database, schema, created_at, updated_at}`. Databases are pages with `is_database:true` and a `schema`.
- **Rows** in databases are pages with `parent_page_id` set to the database page.

## Spec link

This seed implements the Fork Seed pattern. See https://www.ai-nativesolutions.com/spec.html for the full SEED schema and cross-seed mesh protocol.

## License

MIT. See `LICENSE`.

## Built by

Simon Gant · sjgant80@gmail.com · https://www.ai-nativesolutions.com
