# YCA Sports — Static Site Conversion (2026-07-07)

## Goal
ycasports.com must look complete and trustworthy for Apple Developer Program
(organization) enrollment review, and later App Store / Play Store submissions.

## Problems with the current page
- Rendered client-side by `support.js`, which loads React + ReactDOM + Babel
  from unpkg.com at runtime. Without JS (or if unpkg is slow/blocked) visitors
  see raw template markup (`{{ accent }}`, `sc-for`, …).
- No `<title>`, meta description, favicon, Open Graph tags, `lang` attribute.
- Inconsistent contact e-mail: `hello@ycasports.com` displayed, but `mailto:`
  links point to `developer@ycasports.com`.
- No privacy policy page (required later for App Store / Play Store listings).

## Decisions (confirmed by owner)
1. Convert to clean static HTML — same visual design, no JS runtime dependency.
2. Official contact e-mail everywhere: **developer@ycasports.com**.
3. Add an English privacy policy page at `/privacy`, linked from the footer.

## Deliverables
- `index.html` — static, semantic, single file; design preserved (Space
  Grotesk / Instrument Sans / IBM Plex Mono via Google Fonts, purple/orange
  palette); adds title, meta description, canonical, OG/Twitter tags,
  JSON-LD Organization, favicon, responsive nav, focus styles.
- `privacy.html` — same design language; generic company + mobile-app privacy
  policy (served as `/privacy` by Cloudflare Pages clean URLs).
- `favicon.svg` — simple brand monogram (dark plum square, Y + orange dot).
- `support.js` removed (no longer referenced).

## Verification
Render both pages locally in Chrome at desktop (1440px) and mobile (375px)
widths, compare against screenshots of the live site, check all links and
mailto targets.
