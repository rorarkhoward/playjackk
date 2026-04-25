# Blackjack Pro Trainer

A web-based blackjack basic-strategy trainer that grades your decisions against the **Stake v9.10 bot** strategy logic and shows a faithful **Blackjack Apprenticeship** chart for reference.

- ✅ Mobile + laptop optimised — no scrolling on the Train page
- ✅ Full BJA-style strategy chart (Pairs / Soft / Hard / Surrender)
- ✅ Comprehensive stats (per-hand-type accuracy, current/best streak, last-50 visual history, top mistakes)
- ✅ Single self-contained `index.html` — no build step

## Quick deploy on GitHub Pages

1. **Create a new repo** on GitHub (e.g. `blackjack-trainer`) — public, no README.
2. **Upload `index.html`** to the repo root (drag-and-drop in the GitHub web UI, or use `git push`).
3. Go to **Settings → Pages**.
4. Under "Build and deployment", set **Source = Deploy from a branch**, **Branch = `main`** (or `master`), **Folder = `/ (root)`**, then click **Save**.
5. Wait ~30 seconds. GitHub will give you a URL like:
   `https://<your-username>.github.io/blackjack-trainer/`
6. Open that URL on your phone or laptop. Done.

### Custom domain (optional)
In Settings → Pages, add your domain under "Custom domain", then add a `CNAME` record at your DNS provider pointing to `<your-username>.github.io`.

## Other ways to share

| Method | How | Best for |
|---|---|---|
| **GitHub Pages** | as above | Free permanent URL |
| **Netlify Drop** | drag `index.html` onto netlify.com/drop | Instant URL, no signup needed |
| **Cloudflare Pages** | upload via dashboard | Fast CDN, free tier |
| **Vercel** | `vercel deploy` from terminal | Quickest CLI deploy |
| **Local file** | open `index.html` directly | Zero hosting — just double-click |
| **WhatsApp / Telegram** | send the file | One-off share with a friend |

For all hosted options the file is **just `index.html`** — no other files needed.

## Local development

```bash
git clone https://github.com/<your-username>/blackjack-trainer.git
cd blackjack-trainer
# Just open index.html in a browser, or:
python3 -m http.server 8000
# then visit http://localhost:8000
```

## How it works

- **Strategy engine** (`getRecommendedMove`) is a verbatim port of the Stake v9.10 bot's strategy function (DAS enabled). Returns one of: `SP`, `S`, `D`, `Ds`, `H`.
- The **Train** page deals random hands from a 6-deck shoe and validates your move against the engine.
- The **Chart** page renders the Blackjack Apprenticeship basic-strategy chart (Pair Splitting + Soft + Hard + Late Surrender) — purely informational; the trainer doesn't grade surrender since the Stake engine doesn't surrender either.
- The **Stats** page tracks everything in `localStorage` (per device, per browser).

## Strategy reference (DAS)

| Hand type | Quick rule |
|---|---|
| Always split | A,A and 8,8 |
| Never split | 5,5 (treat as hard 10) and 10,10 |
| Hard 17+ | Stand |
| Hard 12–16 | Stand vs 2–6, Hit vs 7–A (12 hits vs 2,3) |
| Hard 11 | Always Double |
| Soft 19 | Stand (Double if dealer 6) |
| Soft 18 | Double 2–6, Stand 7–8, Hit 9–A |

## License

MIT — do whatever you want, just don't blame me when you lose at the casino.
