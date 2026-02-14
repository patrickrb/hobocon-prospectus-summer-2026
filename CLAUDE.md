# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the **Hobocon 2026 Sponsor Prospectus** — a single-page HTML/CSS document designed to render as an 8-page, letter-size PDF. Hobocon is a hacking conference on an Amtrak train, organized under SecKC.org (a 501(c)(3) non-profit).

## Architecture

- `index.html` — The entire prospectus. Self-contained HTML with embedded CSS. No external stylesheets, no JavaScript, no build step.
- `images/` — Photos from the inaugural Hobocon I trip (December 2025, KCY to STL). Used as `<img>` tags with relative paths.
- `Hobocon-2026-Sponsor-Prospectus.pdf` — Generated output PDF.

### Page Structure

The HTML uses a series of `<div class="page">` elements, each sized to exactly 8.5in x 11in via CSS. Pages alternate between `var(--bg-deep)` and `var(--bg-dark)` backgrounds (class `page-dark`). There are no scroll animations, navigation, or interactive elements — everything is static and print-optimized.

**Pages:** Cover, About, Journey (timeline), Inaugural Trip (stats+photos), Why Sponsor (6 cards), Sponsor Tiers (3 tiers), A La Carte, Contact

### Design System

- Dark theme with amber (`#f59e0b`) and cyan (`#06b6d4`) accents
- Fonts: Playfair Display (headings), Inter (body), JetBrains Mono (labels/code)
- All fonts loaded from Google Fonts — requires internet for first render
- CSS uses `print-color-adjust: exact` for dark backgrounds in PDF

## Generating the PDF

```bash
"/Applications/Microsoft Edge.app/Contents/MacOS/Microsoft Edge" --headless --disable-gpu --print-to-pdf="/Users/patrickburns/Projects/hobocon-prospectus/Hobocon-2026-Sponsor-Prospectus.pdf" --no-margins --print-background "file:///Users/patrickburns/Projects/hobocon-prospectus/index.html"
```

Any Chromium-based browser works. The `--no-margins` and `--print-background` flags are required to preserve the dark design and page sizing.

## Key Content Details

- **Contact email:** hobocon@seckc.org
- **Org:** SecKC.org, 501(c)(3) non-profit
- **Event:** Summer 2026, private Amtrak car, Kansas City to Chicago (~11hr), 60 attendees
- **Sponsor tiers:** Pass the Hat ($500+), Conductor ($1,500), Railroad Baron ($3,000)
- **A la carte items:** Lunch, Hotel Shuttle, Pub Crawl, Blinky Badge, Custom
