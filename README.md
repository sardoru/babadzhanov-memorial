# Gulom Bobojonov Memorial

**🌐 Live: [www.gulam-babodjanov.com](https://www.gulam-babodjanov.com)**

A memorial website dedicated to **Gulom Bobojonov (1907–1955)** — orphan, scholar, rector, and pioneering scientist of silk from the village of Ikan near Turkestan, South Kazakhstan.

![OG Preview](og-image.png)

## About

Gulom Bobojonov rose from a peasant village orphan to become one of Central Asia's foremost agricultural scientists. Losing his father at age one, raised by his grandfather and then his mother, he fought through poverty and famine to earn an education. He became a rector, a candidate of agricultural sciences, and a leading authority on sericulture (silk science).

During WWII, his research on parachute silk directly served the Soviet military effort — making him one of two Umarov family great-grandfathers who served at the highest levels of the Uzbek SSR during wartime (alongside Amin Niyazov, the republic's financial commissar).

He died on May 21, 1955, at just 47–48 years old, leaving behind his wife Habiba and seven young daughters.

## Features

- 📖 **Full biography** — From orphaned childhood in Ikan to rector and scientist
- 🏘️ **Ikan section** — History of the ancient village near Turkestan
- 🐛 **Sericulture science** — His contributions to silk research
- 📸 **Photo gallery** — Historical photographs from family archives
- ⏳ **Interactive timeline** — Key life events
- 🌍 **3 languages** — English, Russian, Uzbek
- 🌓 **Dark/light mode** — System-aware with manual toggle
- 📱 **Fully responsive** — Mobile-first design
- ⚡ **Static site** — Single HTML file, no build step

## Life Timeline

| Year | Event |
|------|-------|
| 1907 | Born in Ikan, near Turkestan |
| 1908 | Father dies — raised by grandfather, then mother |
| 1920s | Survives famine, earns education |
| 1930s | Rises through agricultural academy system |
| 1940–1945 | Parachute silk research for WWII military effort |
| 1955 | Dies at age 47–48, leaving wife and 7 daughters |

## Tech Stack

- Pure HTML/CSS/JavaScript (no framework)
- Hosted on [Vercel](https://vercel.com)
- Custom domain via Vercel DNS
- SVG favicon, Gemini-generated OG image

## Family

Gulom Bobojonov is the great-grandfather of the Umarov family. His line of science connects with the Niyazov line of statesmanship through marriage.

**Related memorials:**
- [Aminjan Niyazov](https://www.amin-niyazov.com) — First Secretary of CP Uzbekistan (1903–1973)
- [Giyas Umarov](https://www.giyas-umarov.com) — Founder of Heliotechnology, Academician (1921–1988)

## Documentary film

**"The Mulberry Tree" / «Тутовое дерево»** (2026) — English 15:30, Russian 16:44 — plays in the `#film` section (first in the article, with a "Film" nav link and a "Watch the documentary" button in the hero). The Russian page plays the Russian film; the English, Uzbek and Spanish pages play the English film; the visitor can switch with the English / Русский buttons.

- **Video files:** public Vercel Blob store `babadzhanov-films` (`store_cUew28aNCrwUREQS`, region fra1, connected to this project):
  - `https://cuew28ancrwureqs.public.blob.vercel-storage.com/films/the-mulberry-tree-en-2026-11-25b.mp4`
  - `https://cuew28ancrwureqs.public.blob.vercel-storage.com/films/the-mulberry-tree-ru-2026-11-25b.mp4`
  - H.264 1920×1080 (CRF 21) + AAC 160 kb/s, fast start; 1-year cache.
  - `…-2026-11-25b.mp4` = v3 (25 Nov 2026): the 1929 plate at 3:20 / 3:30 upright; Russian «Ика́на» at 4:50 re-voiced. The v2 files (`…-2026-11-25.mp4`) stay in the store, unreferenced.
- **Posters and subtitles** are in `film/` (`poster-en.jpg`, `poster-ru.jpg`: the title card of each film; `.vtt` subtitles).
- **Standalone watch pages, one per language:** [`/film/en`](https://www.gulam-babodjanov.com/film/en) and [`/film/ru`](https://www.gulam-babodjanov.com/film/ru) (`film/en/index.html`, `film/ru/index.html`, self-contained). `/film` redirects to `/film/ru` when the browser prefers Russian, otherwise to `/film/en` (`vercel.json`).
  - Clickable chapters and a clickable transcript (years and dates in digits; everything else as narrated) that move the player; the address bar follows, so any moment can be shared.
  - **Time links:** `/film/en?t=74` — also `?t=1m14s`, `?t=1:14` or `#t=74` — open the film cued at that moment. The **Share** button copies the page link (or opens the phone's share sheet), with **Start at** adding the current time.
  - **Link previews:** custom cards `film/og-en.jpg` / `film/og-ru.jpg` (1200×630) plus `og:video` tags; JSON-LD `VideoObject` with the chapters as `Clip`s (Google "key moments").
  - The pages and cards are generated from the film's own timing data by `project/make_site_pages.py` and `project/make_og.py` in the film's working folder (not in this repo). Small text changes can be made directly in the HTML.
- **Per-language memorial links:** `/?lang=ru` (or `uz`, `es`, `en`) opens the memorial in that language.
- **To replace a film:** upload the new file under a **new dated pathname** (the old URL is cached for a year), then update the URLs in `index.html` — the `FILMS` table in the script, the `<source>` in the `#film` section and the JSON-LD `VideoObject`s — and the durations in the labels (`hero_watch`, the switch buttons, JSON-LD `duration`).
  ```bash
  vercel env pull .env.local          # in a scratch folder linked to this project, NOT in the repo
  vercel blob put film.mp4 --pathname films/the-mulberry-tree-en-YYYY-MM-DD.mp4 --cache-control-max-age 31536000 --content-type video/mp4
  rm .env.local
  ```

## Deploy

Pushing to `main` deploys production (Vercel Git integration). Manual deploy:

```bash
npx vercel --prod
```

## License

© 2024 Umarov Family. All rights reserved.
