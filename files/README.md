# Your Links Page

A single-file, no-build-tool link page (like Linktree/Beacons), fully responsive
on desktop and mobile. Everything lives in `index.html` — no dependencies to
install, no framework.

## 1. Edit your content

Open `index.html` in any text editor:

- **Title / meta description** — top of the `<head>`.
- **Name & tagline** — search for `Your Name` and `Your tagline goes here`.
- **Logo** — by default it's a 2-letter monogram (`YN`) in a dark square.
  To use an image instead:
  1. Put your logo file next to `index.html` and name it `logo.png`.
  2. Replace this line:
     ```html
     <div class="mark" aria-hidden="true">YN</div>
     ```
     with:
     ```html
     <img class="mark-img" src="logo.png" alt="Your Name logo">
     ```
- **Links** — scroll to the `const LINKS = [ ... ]` array near the bottom.
  Each line is one card:
  ```js
  { label: "Instagram", url: "https://instagram.com/yourhandle", icon: "instagram" },
  ```
  Add, delete, or reorder lines freely. Available `icon` values: `instagram`,
  `tiktok`, `youtube`, `x`, `linkedin`, `link` (a generic chain icon for
  anything else — Threads, Spotify, your website, etc).

That's the whole editing surface — no build step, just save the file.

## 2. Push to GitHub

If you haven't already:

```bash
cd linktree-site
git init
git add .
git commit -m "My links page"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

## 3. Turn on GitHub Pages

1. On GitHub, go to your repo → **Settings** → **Pages**.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)` → **Save**.
4. GitHub will give you a URL like `https://YOUR_USERNAME.github.io/YOUR_REPO/`.
   Wait a minute or two and confirm it loads.

## 4. Connect your own domain

**A) Tell GitHub about the domain**
- Still in **Settings → Pages**, under **Custom domain**, enter your domain
  (e.g. `links.yourdomain.com` or `yourdomain.com`) and save.
- This automatically creates a `CNAME` file in your repo containing that
  domain — don't delete it.

**B) Point your DNS at GitHub**

At your domain registrar (Namecheap, GoDaddy, Cloudflare, etc.), add records
depending on which style of domain you're using:

- **Subdomain** (e.g. `links.yourdomain.com`) — add a **CNAME record**:
  | Type  | Host/Name | Value                      |
  |-------|-----------|----------------------------|
  | CNAME | `links`   | `YOUR_USERNAME.github.io`  |

- **Root/apex domain** (e.g. `yourdomain.com`) — add **A records** pointing
  to GitHub's IPs:
  | Type | Host/Name | Value           |
  |------|-----------|-----------------|
  | A    | @         | 185.199.108.153 |
  | A    | @         | 185.199.109.153 |
  | A    | @         | 185.199.110.153 |
  | A    | @         | 185.199.111.153 |

  (You can optionally also add a CNAME for `www` → `YOUR_USERNAME.github.io`
  so both `yourdomain.com` and `www.yourdomain.com` work.)

DNS changes can take anywhere from a few minutes to a few hours to propagate.

**C) Enforce HTTPS**
- Back in **Settings → Pages**, once GitHub verifies the domain, tick
  **Enforce HTTPS**. This gives you a free SSL certificate automatically.

## Notes

- No build tools, no npm install — it's plain HTML/CSS/JS, so any static
  host works if you ever move off GitHub Pages.
- Fonts (Fraunces + Inter) load from Google Fonts via CDN; everything else
  is self-contained in `index.html`.
- Respects `prefers-reduced-motion` and has visible keyboard focus states.
