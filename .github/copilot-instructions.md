# Copilot Instructions - travis3D Website

## Project Overview
A minimalist, responsive portfolio website for a Charlotte NC 3D design studio. No frameworks — pure HTML, CSS, and vanilla JS. Showcases services: product renders, 3D scanning, custom environments, and 3D printing.

## Architecture

### Tech Stack
- **HTML5** semantic markup, no frameworks or build tools
- **CSS**: Single custom stylesheet `style.css` with CSS custom properties
- **JS**: Inline vanilla JavaScript (nav toggle, hero slider, lightbox)
- **Fonts**: Google Fonts — "DM Serif Text" (headings/nav) + "Inter" (body)
- **Deployment**: cPanel via `.cpanel.yml`

### File Structure
```
index.html        — Home: hero slider + 4 feature rows
product.html      — Product Visualization (4 feature rows)
scan.html         — 3D Scanning (2 feature rows)
custom.html       — Custom Creations (2 feature rows)
print.html        — 3D Printing (2 feature rows)
gallery.html      — Image gallery with JS lightbox
about.html        — About page (placeholder)
style.css         — All styles, CSS custom properties
img/              — All image assets
```

## Key Conventions

### Navigation
Every page uses identical `<nav class="site-nav">` markup. The current page's link gets `class="active"`. Index has no active link.

```html
<nav class="site-nav" aria-label="Main navigation">
    <div class="nav-container">
        <a href="index.html" class="nav-logo"><img src="img/logoflatalt4.png" alt="Travis 3D"></a>
        <button class="nav-toggle" aria-label="Toggle navigation">
            <span></span><span></span><span></span>
        </button>
        <ul class="nav-links">
            <li><a href="product.html">Product Visualization</a></li>
            <li><a href="scan.html">Scans &amp; Processing</a></li>
            <li><a href="custom.html">Custom Creations</a></li>
            <li><a href="print.html">3D Printing</a></li>
            <li><a href="gallery.html">Gallery</a></li>
        </ul>
    </div>
</nav>
```

Every page includes this inline JS at the bottom for mobile toggle:
```js
document.querySelector('.nav-toggle').addEventListener('click', () => {
    document.querySelector('.nav-links').classList.toggle('open');
});
```

### Footer
All pages use the same footer:
```html
<footer class="site-footer">
    <p>&copy; 2025 Travis3D, Inc &middot; 704.998.1464 &middot; <a href="mailto:Stravis3D@gmail.com">Stravis3D@gmail.com</a></p>
</footer>
```

### CSS Architecture
- All styles in a single `style.css` — CSS custom properties in `:root` for colors, fonts, spacing
- Colors: `--color-bg: #0a0a0a`, `--color-accent: #00bbf9`, `--color-gold: #fee440`
- Layout: CSS Grid for feature rows, Flexbox for nav and gallery
- Responsive breakpoints: 900px (single column features), 700px (mobile nav), 500px (single column gallery)
- Feature rows use `.feature-row` with `.reverse` class for alternating text/image layout

### Service Page Pattern
Service pages (product, scan, custom, print) follow the same pattern:
1. `.page-header` with `<h1>` title
2. `.features` container with `.feature-row` divs (alternating `.reverse`)
3. Each row: `.feature-text` (h2, p, btn) + `.feature-media` (img, .feature-caption)

### Gallery
- CSS grid gallery (`gallery-grid` / `gallery-item`) with 3-column layout
- Custom vanilla JS lightbox — no external dependencies
- Gallery sections grouped by category with `<h2>` headers

## Common Tasks
- **Adding a page**: Copy structure from any service page; update `<title>`, nav `active` link, content
- **Updating navbar**: Must be updated in ALL HTML files (no templating)
- **Adding gallery images**: Add to `img/`, create `<div class="gallery-item"><img src="..."></div>` in appropriate section
- **Color/style changes**: Edit CSS custom properties in `:root` block of `style.css`
