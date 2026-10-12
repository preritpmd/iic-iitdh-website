# IIC IIT Dharwad

A single-page, WebGL site for the Institute Innovation Council at IIT Dharwad: a live 3D mountain-temple
scene, the council's four-stage pathway, E-Summit history, a campus feed, a project showcase and contacts.

No build step and no server code. It is plain HTML, CSS and JavaScript, with three.js and the Onest font
bundled in this repo, so it makes **no requests to outside hosts**.

## Files

```
index.html                 the whole site (markup, styles, scene code, content logic)
vendor/three.min.js        three.js r150.1 (pinned copy, MIT)
fonts/                     Onest woff2 files + onest.css
data/feed.example.json     format for a live events feed
THIRD_PARTY_NOTICES.md     licences and credits
```

## Run it locally

Open it through a local server (browsers restrict some features on `file://`):

```bash
cd iic-website
python3 -m http.server 8080
# then open http://localhost:8080
```

## Edit the content

Everything is in `index.html`.

| What | Where |
| --- | --- |
| About text, four stages, headings | the `<section id="gate">` markup |
| Council figures (26 / 4 / 2 / 7) | `.gate-stats`, `data-count` attributes |
| E-Summit history | `<div id="esummit">` rows |
| Team | `<div class="team">` |
| Campus feed | `SAMPLE_FEED` in the script, or point `CONFIG.feedUrl` at a JSON file (see `data/feed.example.json`) |
| Project showcase | `PROJECTS` in the script (**sample entries, replace them**) |
| Contacts | `mailto:` / `tel:` links in the join section and footer |

To drive the feed from a file, set `CONFIG.feedUrl` to `'data/feed.json'` and add that file.

## Data sources and what is still sample

- Real, from IIT Dharwad public pages: E-Summit 2026/2025/2023/2021 details, the council description,
  the outreach contact, the events in the feed, the team list (older IIC members page) and the figures
  (IIC LinkedIn page).
- **Sample:** the eight showcase projects. No public page lists real ones.
- Check the team names and figures with the council before publishing: the sources may be out of date.

## URL options

`?q=low` lighter quality, `?dpr=1` cap pixel ratio, `?post=0` no post-processing, `?shadow=0` no shadows,
`?adapt=0` fixed resolution, `?shot=2` jump to a section (0 to 5).

## Deploy

**GitHub Pages:** push to GitHub, then Settings, Pages, deploy from the `main` branch, root folder.

**IIT Dharwad server:** upload the folder contents so `index.html` is at the site root. It is static, so any
web server works. Hosting on `iitdh.ac.in` needs a request from the faculty in charge to the institute's
web or IT team; confirm the exact process with them.

## Requirements

A browser with WebGL2. Without WebGL the page falls back to a static, readable layout.

## Licence

Not chosen yet. Add a `LICENSE` file once the template licence in `THIRD_PARTY_NOTICES.md` is confirmed.
