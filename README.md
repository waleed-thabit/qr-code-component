# Frontend Mentor - QR code component solution

This is a solution to the [QR code component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/qr-code-component-iux_sIO_H). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [AI Collaboration](#ai-collaboration)
- [Author](#author)

## Overview

### Screenshot

Mobile:

![Mobile layout](./assets/preview/screenshot-1.png)

Desktop:

![Desktop layout](./assets/preview/screenshot-2.png)

### Links

- Solution URL: [https://github.com/waleed-thabit/qr-code-component](https://github.com/waleed-thabit/qr-code-component)
- Live Review URL: [https://waleed-thabit.github.io/qr-code-component/](https://waleed-thabit.github.io/qr-code-component/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Mobile-first workflow
- Vanilla HTML and CSS only, no frameworks

### What I learned

**1. Centering an element without a scrollbar.**

My structure was a `main` container holding the card (an `article`), and a `footer` placed directly inside the `body`. At first I gave the `main` a `min-height: 100dvb`, but because the footer sat below it, the page became taller than the screen and a scroll appeared. I patched it with `min-height: 98dvb`, but that is just a hack that breaks on other screens.

The proper fix: make the `body` a flex column with the full screen height, and let the `main` take all the remaining space with `flex: 1`. Then I center the card inside it.

```css
body {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  min-height: 100dvh;
}

main {
  display: grid;
  flex: 1;
  place-items: center;
}
```

This way the footer keeps its own space, the `main` fills the rest, and the card stays centered with no scroll.

**2. `vh` vs `dvh`.** On mobile, `100vh` is the largest possible height (when the browser address bar is hidden), so the page can be taller than the visible area. `100dvh` (dynamic viewport height) adapts to the address bar. I write `100vh` first as a fallback for old browsers, then `100dvh` right after it.

**3. A flexible image.** I first gave the QR image a fixed `300px` width, and the card overflowed on narrow screens (around 320px). Using `width: 100%` together with `max-width: 300px` lets the image shrink with the card and never grow past 300px.

```css
.qr-code-img {
  max-width: 300px;
  width: 100%;
  height: auto;
}
```

**4. Small details that matter:**

- The card title should be an `h1`, because the page needs a top-level heading.
- The `alt` text should describe what the image does ("QR code linking to Frontend Mentor"), not just its type.
- Use `rem` instead of `px` for sizes and font sizes, so the page respects the user's browser font size.
- Keep colors in CSS variables, including the link color.

### AI Collaboration

I did not use AI to build the first version of this project. I used **Claude** to help me write this README, and to review my finished code. It pointed out the image overflow on narrow screens, the `vh` / `dvh` difference, the `h1` heading and the `alt` text, and I applied these fixes myself.

## Author

- GitHub - [@waleed-thabit](https://github.com/waleed-thabit)
- Frontend Mentor - [@waleed-thabit](https://www.frontendmentor.io/profile/waleed-thabit)
