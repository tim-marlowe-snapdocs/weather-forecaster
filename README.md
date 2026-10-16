# Weather Forecaster: Pick the Forecast

A self-contained, zero-dependency HTML teaching game about overfitting and the
bias–variance tradeoff, built for a non-technical audience. The entire game is
`index.html` — open it in any browser, no build step.

**Play it:** https://tim-marlowe-snapdocs.github.io/weather-forecaster/

Three forecasters each fit the same recorded week, then project the coming days:
Straight-Line Steve (a ruler), Trend-Spotter Tess (follows the real shape), and
Dr. Wiggles (threads every recorded dot). Pick who you trust for the days nobody has
seen yet. The curve that best explains the past is usually not the one that predicts
the future — that gap is the lesson.

## Editing

`index.html` is the single source of truth. GitHub Pages serves it from the root of
`main`, so **merging to `main` publishes automatically** (first build takes a minute).

Work on branches, not directly on `main`:

```sh
git switch -c tweak-tess-swing      # new branch
# edit index.html, test by opening it locally in a browser
git commit -am "Moderate Tess end-swing"
git push -u origin tweak-tess-swing
gh pr create --fill                 # open a PR
# merge the PR -> main -> site redeploys
```

To preview locally just open the file (`open index.html`) — it needs no server.

## Leaderboard

High scores are stored in Supabase via the project's **anon public** key (embedded in
`index.html`, RLS-protected — safe to ship). The `weather_scores` table has anon
`insert` and `select` policies; nothing sensitive is stored.
