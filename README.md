# DealSift

Compares weekly grocery deals and everyday prices at Kroger, Publix, Aldi and Trader Joe's, with ZIP code and distance filtering.

It is one self-contained file (`index.html`). There is nothing to install or build.

## Put it online with GitHub Pages (free)

1. Sign in at github.com and click **New repository**. Name it (for example `dealsift`), keep it **Public**, and create it.
2. Click **Add file > Upload files**, drag in `index.html` and `.nojekyll` (and this README if you like), then **Commit changes**.
3. Open **Settings > Pages**. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose branch **main** and folder **/ (root)**, and click **Save**.
4. Wait about a minute. Your site will be at `https://YOUR-USERNAME.github.io/dealsift/`.

To preview on your own computer first, just double-click `index.html`.

## Updating the data

All data is inside `index.html` as plain text. Search the file for these names:

- `AD_RAW` is the list of deals and prices, one item per line:
  `category|name|deal|save-or-regular|note`
  - Category codes: F Frozen, G Grocery, H Health & Nutrition, B Bakery, S Snacks, P Pantry, D Dairy & Eggs, M Meat & Seafood, R Produce, V Beverages
  - Deal codes: `bogo`, `b2g1`, `b2g2`, `b2g3` (buy 2 get 1/2/3 free), `p9.99` (price, with optional save-up-to amount in the next field), `m2/10` (2 for $10), `o25` (25% off), `d1.50` (coupon $ off), `k2.84` with regular price in the next field (Kroger), `q`/`a` (same for Publix/Aldi), and text labels `t:`/`u:` (Publix), `y:`/`z:` (Aldi), `w:` (Trader Joe's everyday price). A leading `~` means the deal runs to 11/3.
- `CMP_RAW` is the "Compare stores" list. One line per product: `name|category|unit|k=price/quantity~product note;p=...;a=...;t=...` (k Kroger, p Publix, a Aldi, t Trader Joe's). Quantity is in the unit (oz, lb, fl oz, or each), and the app works out the price per unit.
- `SL` is the store location list: `[chain, "name", "address", lat, lng]`. Chain numbers: 0 Kroger, 1 Publix, 2 Aldi, 3 Trader Joe's.
- `ZIPS` holds ZIP code centers. ZIPs that contain a store in `SL` work automatically.

After editing, commit the change on GitHub and the site updates in about a minute. Weekly ads change every week, so the deal lines need refreshing weekly.

## Good to know

- Prices come from store ads and websites collected in October 2026. They can be out of date or differ by store.
- Store locations are limited to Georgia's main cities plus Charlotte, Nashville, Tampa and Orlando.
- Distances are straight-line, not driving distance.
