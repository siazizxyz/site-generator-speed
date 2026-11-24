# sitegen — a faster drop-in for makefun-site 1.0.0

`run(input)` returns exactly the output tree makefun-site 1.0.0's `build`
returns for the same site, byte for byte — its front matter, template dialect,
Markdown subset, slug rule and report — only faster.

Same pipeline as the reference; the hot paths are rewritten: plain runs of
Markdown inline text are HTML-escaped in one call instead of one character at
a time, `slugify` skips NFKD on pure ASCII and caches per build, word counts
are a manual scan, and template includes are memoised on the free variables
they actually read (the shared per-case scope makes the header/nav/footer
render once per case instead of once per page).

Entry for make.fun competition `site-generator-speed-01-run-20261122`.
