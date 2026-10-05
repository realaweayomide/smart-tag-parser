# Smart Tag Parser

Turn messy CRM tags and free-text into clean, structured fields — **entirely in the browser**. No server, no API key, no data leaves the page.

**[▶ Live demo](https://realaweayomide.github.io/smart-tag-parser/)** · built by [Ayomide Awe](https://github.com/realaweayomide)

## The problem

Most CRMs can't extract structured data that lives *inside* a free-text tag. A contact tagged
`referral: us business funding llc (george otel)` and `sell-price-9000` is useless until someone
reads it and re-types the pieces into the right fields. At scale, that's hours of manual data entry —
or data that just never gets captured.

## What it does

Paste the raw tags/notes, and it extracts:

| Field | From | Example |
|---|---|---|
| Sell price | `sell-price-9000`, `sell price: 9000`, `$9,000` | `$9,000` |
| Referral partner | `referral: us business funding llc` | `US Business Funding LLC` |
| Contact | `referral: … (george otel)` | `George Otel` |
| Email / Phone / Tier / Status / Source / Date | loose patterns | normalized |

Names are title-cased, entity suffixes (`LLC`, `INC`, `LLP`) are upper-cased, prices are formatted.
Output is shown as clean fields **and** copyable JSON.

## How it works

Pure client-side JavaScript — a set of focused regular expressions plus a normalization pass
(`titleCase`, `money`). It parses live as you type. See [`index.html`](index.html) — it's one file.

## Run it

Just open `index.html` in any browser. That's it. (Works offline.)

## Why I built this

This is a generic, open-source version of a webhook enrichment service I built for a client whose
CRM couldn't parse data out of its own tags. The production version runs as a secured webhook that
writes the parsed fields back to the CRM via its API; this demo shows the parsing core.

## License

MIT
