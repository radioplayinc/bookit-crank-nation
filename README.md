# Crank Nation Studios — Bookit studio booking demo (Tier 0)

No-scroll Bookit booking app for Crank Nation Studios, Beltsville, MD.
Built from the Amplitude Studios studio template, reskinned to Crank Nation's
gold/black logo (ink #14100A, brand + signal #D9A400, both swapped).

## Flow

Loader (supplied logo) → project (Single / Album / EP / Podcast / Voiceover /
Something else) → session → then one of two paths:

- Recording path: Crank Nation Studio ($60/hr) → hours (1 / 2 / 4 / 8, no
  discount) → date + start time → contact → estimate → demo booking →
  confirmation CN-#### with gold confetti + downloadable PNG session sheet.
- Service path: Mixing $80/song / Mastering $50/song / Mix + Master $130/song /
  Exclusive beat $200/beat → song/beat stepper → date + start time →
  contact → estimate → demo booking → confirmation.

No add-ons screen: no add-on rates were found in the studio's published
pricing, so none are invented. No block or multi-song discount: none is
published, so none is applied. Schedule times are demo availability — the
studio confirms the final time; no opening hours are claimed.

## Rates — source and status

Rates are the studio's published pricing as quoted in a Voyage ATL interview
with founder Mic Kartel (Hip Hop, R&B, Soul, Pop, Reggae; beats, recording,
mixing, mastering):

- Recording studio time: $60/hr, mixing and mastering included
- Mixing: $80/song
- Mastering: $50/song
- Mix + Master: $130/song (the $80 + $50 sum, shown as such)
- Exclusive beat: $200/beat

That interview is older (~2022), so these rates are the best published
source found, NOT a fresh confirmation from the studio. Confirm them with
the studio before this goes to a real customer or a paid booking.

Address and phone are from a public business listing for Crank Nation
Studios LLC: 4600 Powder Mill Rd, Beltsville, MD, (301) 955-6914.
Confirm both with the studio before pitching — the listing is not the
studio's own site, and no studio email was found.

## Backend — Tier 0 demo

Front-end only. A demo booking is saved nowhere, emailed nowhere, and
texted nowhere. The confirmation screen says so, the downloadable session
sheet is the only record, and it disappears when the tab reloads. No
payment is taken, no invoice is promised, and no Jim deposit link is wired.

Backend destination is undecided: Apps Script (Sheet + Calendar + email)
vs Supabase is still Basqi's call. Do not present this as a live booking
site until that choice is made and a test booking passes.

## QA cases (math, verified by static check + artifact audit)

- Recording 4 hours: 4 x $60 = $240
- Mixing 3 songs: 3 x $80 = $240
- Mix + Master 2 songs: 2 x $130 = $260
- Exclusive beat 1: $200; recording 8 hours: $480

Headless Puppeteer QA could not run in this session: the local Chromium
launch is blocked by the image's WebGL domain policy ("Hatch WebGL domain
policy is required for browser startup"). JS parses clean (node --check),
all JS element references resolve, all data-next targets exist, no HTML
comments, and FAQ answers are byte-identical across JSON-LD (index),
JSON-LD (faq.html) and visible faq.html copy. The phone-review artifact
audit is the live-flow check for this build.

## Files

- `index.html` — the app (single file, vanilla JS, Manrope + IBM Plex Mono)
- `logo.jpg` — supplied logo; `icon-192.png`, `icon-512.png`,
  `apple-touch-icon.png`, `og-image.jpg` — generated from it
- `faq.html`, `sitemap.xml`, `robots.txt`, `llms.txt` — SEO pack
  (LocalBusiness schema; intended Pages URL bookit-crank-nation.pages.dev,
  NOT live until Pages is connected)
- `manifest.webmanifest`
- `qa/qa.js` — headless QA script for when the Chromium launch works again

## Before it goes live for the studio, fill these

- Confirm current rates, address, phone, and email with the studio
- Backend tier decision (Apps Script vs Supabase) + test booking
- Jim deposit link, if a deposit is wanted (no deposit policy was published)
- Pages connect (repo radioplayinc/bookit-crank-nation, preset None, output /)
  then verify from production HTML, plus Search Console / Bing sitemap submit
