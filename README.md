# Kimberly Glazing & Industrial Supply Inc. — Website

Single-file static site. Everything (HTML, CSS, JS, logo SVG, favicon) lives in `index.html`. No build step, no dependencies except Google Fonts.

## Deploy (GitHub + Vercel)

1. Create a new GitHub repo and add `index.html`.
2. In Vercel: **Add New → Project → Import** the repo.
3. Framework preset: **Other**. Build command: *(leave empty)*. Output dir: `./`.
4. Deploy. That's it — Vercel serves `index.html` at the root.

To use a custom domain (e.g. `kimberlyglazing.ph`), add it under **Project → Settings → Domains**.

## Add your real project photos

The site uses a pure-CSS "glass" look instead of stock images, so nothing is broken or placeholder. When you want real photos in the **Work** section:

1. Drop images into an `/images` folder in the repo.
2. In `index.html`, find the `<!-- WORK -->` section. Swap the client-name marquee for `<img>` tags, or add a simple grid above it:
   ```html
   <img src="images/popeyes-sto-tomas.jpg" alt="Popeyes — SM Sto. Tomas" loading="lazy">
   ```
3. Keep images optimized (≤ 300 KB, WebP if possible) for performance.

## Wire the contact form (optional)

Right now the form opens the visitor's email app via `mailto:` — works instantly, no backend. To collect submissions automatically instead:

- **Formspree (easiest):** create a form at formspree.io, then in `index.html` find the `<form>` and set `action="https://formspree.io/f/XXXX"` and `method="POST"`. Remove the `mailto` JS handler (it's commented where to do this).
- **Vercel:** add a serverless function in `/api/contact.js` and point the form `action` to `/api/contact`.

## Moving to WordPress / Elementor later

The page is built as clean, self-contained sections so each maps to one Elementor section:

| Site section | Elementor build |
|---|---|
| Header / nav | Theme Builder → Header |
| Hero ("Goes beyond the usual") | Section, 2 columns; heading + glass visual |
| About + stats | Section, 1 col text + inner counter widgets |
| Services | Section with an Icon List or a 2-col text block (no boxes) |
| Brands (Grandeur / Digicote / Prism) | Dark section, 3 inner columns with vertical dividers |
| Work / clients | Section + Marquee/Logo-carousel widget |
| Contact | 2 cols: office details + Form widget |
| Footer | Theme Builder → Footer |

Copy the color values and font choices below into Elementor's Site Settings so the brand stays consistent.

### Brand reference

- **Red** `#E11C24` (use `#C2161D` for small red text on white — better contrast)
- **Blue** `#16A2DE` / deep `#0E7FB4`
- **Navy** `#08182E`
- **Paper** `#F4F7FB`
- **Fonts:** Archivo (headlines), Inter (body), IBM Plex Mono (labels/specs)
