# WebPerf Guide

Add your own URLs to test in a \_data/sites/\*.js configuration file. Look at the existing samples (Make sure you use skip: false). You can delete the existing ones after you’ve made your own

- Requires Node 12+
- Each file in `_data/sites/*.js` is a category and contains a list of sites for comparison.

## Run locally

_After cloning you’ll probably want to delete the initial `_data/sites/*.js` files and create your own file with a list of your own site URLs!_

```
npm install
npm run test-pages
npm run start
```

## Deploy to Netlify

Can run directly on Netlify (including your tests) and will save the results to a Netlify build cache (via Netlify Build Plugins, see `plugins/keep-data-cache/`).

_After cloning you’ll probably want to delete the initial `_data/sites/*.js` files and create your own file with a list of your own site URLs!_

WebPerf will also save your data to `/results.zip` so that you can download later. Though this has proved to be unnecessary so far, it does serve as a fallback backup mechanism in case the Netlify cache is lost. Just look up your previous build URL and download the data to restore.

**Run every day or week**: You can set WebPerf to run at a specified interval using a Netlify Build Hook, read more on the Eleventy docs: [Quick Tip #008—Trigger a Netlify Build Every Day with IFTTT](https://www.11ty.dev/docs/quicktips/netlify-ifttt/).

## Known Limitations

- If you change a URL to remove a redirect (to remove or add a `www.`, moved domains, etc), you probably want to delete the old URL’s data otherwise you’ll have two entries in the results list.
- When running on Netlify, a single category has a max limit on the number of sites it can test, upper bound on how many tests it can complete in the 15 minute Netlify build limit.
- The same URL cannot be listed in two different categories (yet).
