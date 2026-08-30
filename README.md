# Zainab Shaikh: Portfolio Website

A single-page personal portfolio built from scratch with HTML, CSS, and vanilla JavaScript. No frameworks, no libraries.

**Live site:** https://zenab-s.github.io/portfolio-website/

## About This Project

This portfolio was built section by section as a learning project. The goal wasn't just to end up with a finished site, but to genuinely understand how every part of it works. Each feature (layout, responsiveness, interactivity) was built incrementally, with the reasoning behind each decision worked through before writing the code.

## Features

- Responsive layout that adapts across desktop, tablet, and mobile (Flexbox + CSS Grid + media queries)
- Custom color system built with CSS variables for easy theming
- Google Fonts typography with a dedicated heading/body font pairing
- Mobile hamburger navigation menu (vanilla JS toggle)
- Custom-built smooth scroll animation with controllable duration (`requestAnimationFrame`)
- Scroll-based active navigation highlighting
- Fixed/sticky navbar
- Fully keyboard-navigable, with verified WCAG-AA color contrast

## Tech Stack

- **HTML5**: semantic structure (`<section>`, `<header>`, `<nav>`)
- **CSS3**: Flexbox, Grid, custom properties (CSS variables), media queries, transitions
- **Vanilla JavaScript**: no frameworks or libraries; DOM manipulation, event listeners, `requestAnimationFrame`
- **Google Fonts**: loaded via `<link>` with `preconnect` and `display=swap` for performance
- **GitHub Pages**: static hosting/deployment

## Project Structure

```
portfolio/
│
├── index.html
├── css/
│   └── style.css
├── js/
│   └── script.js
├── assets/
│   └── images/
│       └── profile_avatar.jpg
└── README.md
```

## Sections

Hero, About, Experience, Projects, Technical Skills, Education, Contact

Content is pulled directly from my CV, with no invented achievements or projects. Projects are grouped by category (Machine Learning & CS, Game Development, C++ / OOP & Data Structures) rather than listed as one long flat list.

## Notable Technical Decisions

**Single-page architecture over multi-page.** I considered a traditional multi-page site (separate `about.html`, `projects.html`, etc.) versus a single scrollable page with anchor-linked sections. From a networking standpoint, a single page pays a slightly heavier cost on the first load (one HTTP request for everything), but every subsequent navigation is instant: just the browser scrolling to an anchor, with zero further network requests. A multi-page site is lighter per page, but every click is a fresh round trip, involving a DNS lookup, a TCP handshake, and a full request/response cycle. For a project this size, with minimal media and mostly text content, the single-page approach wins: one load under a second, then no further network activity while browsing. I'd choose multi-page only for a much larger site with genuinely heavy, distinct content per page.

**CSS Grid for the project cards, Flexbox for the skill tags.** These look similar (rows of boxes) but needed different tools. Grid was right for the project cards because I wanted a fixed, predictable 3-column structure, and I accepted that a category with only 2 cards would leave a visible empty slot rather than force artificial centering. Flexbox was right for the skill tags because tag lengths vary wildly ("C" vs. "Autodesk Fusion 360"), and a growing list of skills over time needs to flow and wrap naturally rather than be squeezed into equal-width grid columns.

**Custom JavaScript scroll animation instead of CSS `scroll-behavior: smooth`.** CSS's built-in smooth scroll works, but the browser controls the speed with no way to adjust duration. To get a slower, more deliberate scroll, I wrote a small animation loop using `requestAnimationFrame` that calculates the scroll position roughly 60 times per second based on elapsed time versus a set duration. This traded a one-line CSS solution for more code in exchange for actual control over the feel of the interaction.

**CSS variables (`:root` custom properties) for the entire color system.** Every color on the site, including backgrounds, accents, and text, is defined once in `:root` and referenced everywhere else with `var(--color-name)`. This meant the whole site's palette could be changed in one place while iterating on design direction, rather than hunting through the file for every hardcoded hex value.

**Contrast verified, not assumed.** Text/background color pairs were checked against the actual WCAG 2.0 luminosity formula (4.5:1 minimum for normal text) rather than judged by eye. A color combination can look subjectively "blendy" while still measuring as high-contrast, since contrast ratio is about luminance (brightness), not hue similarity.

## Running Locally

1. Clone the repo
2. Open the folder in VS Code
3. Right-click `index.html` and choose "Open with Live Server" (requires the Live Server extension)

No build step, no dependencies to install. It's plain HTML/CSS/JS.

## Author

Zainab Shaikh, LUMS Class of 2028, BS Computer Science
[GitHub](https://github.com/zenab-s) · [LinkedIn](https://www.linkedin.com/in/zainab-shaikh-9ab079291/) · [Itch.io](https://zs2000.itch.io/)