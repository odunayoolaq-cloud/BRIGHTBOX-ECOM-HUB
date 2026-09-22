# Brightbox Ecom Hub — Landing Page

A single-page, self-contained static website. Everything the page needs —
CSS, JavaScript, and every proof/founder image — is inlined into the one
`index.html` file. There is no build step, no `package.json`, and no
bundler involved.

## Files

```
index.html   ← the entire site (structure, styles, script, images)
README.md    ← this file
```

That's it. One file is the whole deployable project.

## Dependencies

Because everything is inlined, there is nothing to install and nothing
that can go "missing." The only things the page reaches out to at
**runtime**, in a visitor's browser, are:

| What | Why | Required? |
|---|---|---|
| `fonts.googleapis.com` / `fonts.gstatic.com` | Loads Space Grotesk + Inter | Falls back to system sans-serif if blocked — page still works |
| `formspree.io/f/xjykwajn` | Delivers the application form to `odunayoolaq@gmail.com` | Needed for the form to submit; falls back to opening the visitor's email app if the request fails |
| `wa.me/447838778428` | WhatsApp deep links (Contact Me, post-application redirect, community link) | Needed for those buttons to open WhatsApp |
| `discord.gg/4mxh55hBrc` | Discord invite link | Needed for the Discord button |
| `tiktok.com/@ecomolq` | TikTok profile link | Needed for the TikTok link |

No API keys, no environment variables, no server-side code anywhere.

**Before going live:** log into your Formspree dashboard and confirm the
notification email for form `xjykwajn` — Formspree requires one
confirmation click before it will actually deliver submissions.

## Deploying it

Pick whichever you're already comfortable with — all of these work as-is,
no configuration needed:

### Netlify (easiest)
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag the `index.html` file (or this whole folder) onto the page
3. Done — you get a live URL immediately, and can attach a custom domain in Site settings → Domain management

### Vercel
1. `npm i -g vercel` (one-time)
2. From this folder, run `vercel --prod`
3. Follow the prompts — no build command needed, just a static deploy

### GitHub Pages
1. Create a new repo and push this folder to it
2. Repo Settings → Pages → Deploy from branch → select `main` and `/ (root)`
3. Your site is live at `https://<username>.github.io/<repo>/`
4. (Optional) Add a custom domain in the same Pages settings screen

### Any traditional host / cPanel
1. Upload `index.html` into `public_html/` (or your site's web root)
2. That's the entire deploy — no other files needed

## Editing later

Open `index.html` in any code editor. It's organized top to bottom as:

- `<style>` — all CSS, using a small set of CSS custom properties at the
  top of `:root` for the color palette (edit those to reskin the site)
- `<body>` — the markup, section by section, in the same order they
  appear on the page (nav → hero → learn → how it works → proof →
  why → pricing/offer → apply → community → faq → final CTA → footer)
- `<script>` — the FAQ accordion, mobile menu, marquee, intro
  scramble-text effect, and the Formspree submission handler

Images are embedded directly as `data:image/jpeg;base64,...` strings
inside `<img src="...">` tags — search for `proof-card` in the file to
find each one if you need to swap a screenshot out.
