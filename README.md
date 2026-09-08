# legal

Public policy pages for my published apps, served by GitHub Pages.

Live at <https://siddharthpattnaik.github.io/legal/>

This repo is public **only** so Pages can serve it — no app source lives here.

## Layout

```
index.html            list of apps, linking to each policy
assets/style.css      shared styling for every page
_template/            starting point for a new app (not linked from index.html)
niospdf/               NiosPDF, one page per platform
  privacy-android.html
  privacy-ios.html
  privacy-desktop.html
```

## Adding a new app

1. `cp -r _template <app-slug>` (lower-case, no spaces — it becomes part of the URL).
2. Rename the copied `privacy.html` to `privacy-<platform>.html` (`android`, `ios`, `desktop`)
   if the app ships on more than one platform and its facts differ per platform; a
   single-platform app can stay `privacy.html`. Then replace every ALL_CAPS placeholder:
   `APP_NAME`, `APP_ID`, `APP_SLUG`, `LAST_UPDATED`, `APP_ONE_LINE_DESCRIPTION`,
   the `LOCAL_DATA_ITEM_*`, `PERMISSION_*` / `WHY_*`, and `THIRD_PARTY_PARAGRAPH`.
3. Delete or rewrite any claim in the template that is not true of that app. The template
   assumes an offline, on-device app with no accounts, ads, analytics or crash reporting.
   A policy that overstates privacy is itself a Play policy violation.
4. Add a `<li>` for it in `index.html`.
5. Commit and push. The page is live within a minute or two at
   `https://siddharthpattnaik.github.io/legal/<app-slug>/privacy-<platform>.html`.
6. Paste that URL into Play Console → **Policy → App content → Privacy policy**, and make sure
   the **Data safety** form says the same thing.

## Never change

Once an app is live, keep its folder name and file name stable — the URL is registered in Play
Console, and a 404 there will hold up a review. Edit the page in place and bump "Last updated".
