---
name: apify-store-optimization-expert
description: "Maximize revenue from Apify Store Actors by auditing publication info, README/SEO, monetization, schemas, quality score, pricing, testing, maintenance, and promotion using current Apify documentation and the user's actual Actor."
---

# Apify Store Optimization Expert

Use this skill when the user wants to make more money from Apify Actors, publish an Actor, improve Actor strength or quality score, choose pricing, configure pay-per-event monetization, write Store publication copy, improve README/SEO, add schemas, or promote an Actor.

This is an operator skill, not a generic marketing note. The output should be concrete enough that the user can paste it into Apify Console or implement it in the Actor repository.

## Current Official Sources To Check

Apify Store rules and recommendations change. Before giving final monetization or publication instructions, check the current official docs when network is available:

- Monetization overview: `https://docs.apify.com/platform/actors/publishing/monetize/`
- Pay per event: `https://docs.apify.com/platform/actors/publishing/monetize/pay-per-event`
- Pricing and costs: `https://docs.apify.com/platform/actors/publishing/monetize/pricing-and-costs`
- Publishing overview: `https://docs.apify.com/platform/actors/publishing`
- Actor quality score: `https://docs.apify.com/platform/actors/publishing/quality-score`
- README guide: `https://docs.apify.com/academy/actor-marketing-playbook/actor-basics/how-to-create-an-actor-readme`
- Name and description guide: `https://docs.apify.com/academy/actor-marketing-playbook/actor-basics/actor-description`
- SEO guide: `https://docs.apify.com/academy/actor-marketing-playbook/promote-your-actor/seo`
- Marketing checklist: `https://docs.apify.com/academy/actor-marketing-playbook/promote-your-actor/checklist`
- Product Hunt guide: `https://docs.apify.com/academy/actor-marketing-playbook/promote-your-actor/product-hunt`
- Actor idea validation: `https://docs.apify.com/academy/build-and-publish/actor-ideas/actor-validation`
- Actor URL: `https://docs.apify.com/academy/actor-marketing-playbook/actor-basics/importance-of-actor-url`
- Actor naming: `https://docs.apify.com/academy/actor-marketing-playbook/actor-basics/name-your-actor`
- Input schema UX: `https://docs.apify.com/academy/actor-marketing-playbook/product-optimization/how-to-create-a-great-input-schema`
- Issues tab: `https://docs.apify.com/academy/actor-marketing-playbook/interact-with-users/issues-tab`
- Emails to Actor users: `https://docs.apify.com/academy/actor-marketing-playbook/interact-with-users/emails-to-actor-users`
- Store bio: `https://docs.apify.com/academy/actor-marketing-playbook/interact-with-users/your-store-bio`
- Affiliates: `https://docs.apify.com/academy/actor-marketing-playbook/promote-your-actor/affiliates`
- Actor bundles: `https://docs.apify.com/academy/actor-marketing-playbook/product-optimization/actor-bundles`
- Automated tests: `https://docs.apify.com/platform/actors/development/automated-tests`
- Input schema: `https://docs.apify.com/actors/development/input-schema`
- Dataset schema: `https://docs.apify.com/platform/actors/development/actor-definition/dataset-schema`
- Output schema: `https://docs.apify.com/platform/actors/development/actor-definition/output-schema`
- API/store details if comparing competitors: `https://docs.apify.com/api/v2/store-get`

Use official Apify documentation as primary source. Blogs and help articles are secondary unless they are from Apify and current. If docs conflict, current `docs.apify.com` wins.

## Idea Validation Before Build Or Repositioning

Use this section when the user is choosing a new Actor, deciding whether to publish, or asking how to make more money before there is clear traction.

Validate demand before building or heavily repositioning:

1. SEO demand:
   - Check Google Keyword Planner, Google autocomplete, related searches, and simple keyword tools.
   - Look for multiple related terms such as "`<target> scraper`", "`<target> API`", "`download <target> data`", "`<target> price tracker`".
   - Treat low search volume as niche, not automatically bad; it means direct marketing and community distribution matter more.
2. Trend health:
   - Use Google Trends to distinguish growing demand from declining or one-time viral spikes.
   - Rising low-volume keywords can be better than high-volume declining markets.
3. Community pain:
   - Search Reddit, Hacker News, Stack Overflow, X/LinkedIn, Discord, Facebook groups, and niche forums.
   - Save exact user language and recurring asks. Use that language in Store descriptions, README headings, and examples.
   - Spending signals are strongest: "currently paying $X/month", "upgraded to paid because", competitor pricing mentions, or feature complaints from paying users.
4. GitHub/open-source signals:
   - Stars, star growth, forks, recent commits, high-upvote issues, and unresolved themes can reveal demand and gaps.
5. Product Hunt and broader market:
   - Review recent automation/data launches for taglines, visuals, positioning, and upvote patterns.
   - Search non-Apify SaaS/API competitors because the buyer compares against the full market, not only Apify Store.
6. Apify Store saturation:
   - 1-5 similar Actors: possible blue ocean or unproven demand; validate carefully.
   - 10-30 similar Actors: healthy competition; differentiation is required.
   - 50+ similar Actors: saturated; continue only with an obvious gap, underserved niche, or stronger distribution.
   - If an Apify-maintained leader has very high users and the new Actor has no clear angle, recommend adjacent specialization instead of direct cloning.
7. Direct feedback:
   - Ask likely users if they would use or pay for the exact workflow.
   - Specific questions about pricing, fields, exports, integrations, or limits count more than "sounds interesting".

When optimizing an existing Actor, use the same validation logic to decide whether to improve, niche down, rename, bundle, or build adjacent Actors.

## First Pass

1. Identify the Actor:
   - Actor ID, owner, name, unique name, public/private state, category, pricing model, run count, build count, issues, monitoring status, and current Actor strength or quality score hints.
   - Current Store URL if public.
   - Current README, `.actor/actor.json`, input schema, dataset schema, output schema, key-value store schema, and source files if a repo is available.
2. If the user only pasted Apify Console text or a screenshot, extract the current fields from that evidence and state which fields remain unverified.
3. If the Actor is tied to a repo, read the real files before recommending schema or code edits:
   - `.actor/actor.json`
   - `.actor/input_schema.json` or inline input schema
   - `.actor/dataset_schema.json`
   - `.actor/output_schema.json`
   - README or `ACTOR.md`
   - `src/main.*`, `main.*`, charging helpers, dataset push code, and run limit logic
4. If Apify API access is available through existing env, use it read-only first:

```bash
test -n "$APIFY_TOKEN" && curl -sS "https://api.apify.com/v2/acts/<OWNER>~<ACTOR>?token=$APIFY_TOKEN" | jq '{id,name,title,username,isPublic,stats,pricingInfo}'
```

Do not print token values.

## Revenue Strategy Order

Optimize in this order because each layer compounds the next:

1. Product-market fit: clear use case, narrow enough to rank, broad enough to sell.
2. Reliability: successful runs, default input test, non-empty dataset, graceful partial failures.
3. Ease of use: self-explanatory inputs, strong defaults, sample input, no surprise auth/setup.
4. Output clarity: dataset schema, output schema, useful fields, export-friendly results.
5. Pricing transparency: predictable PPE or pay-per-usage costs with examples.
6. Store conversion: name, description, icon, categories, screenshots/video if available, README.
7. SEO acquisition: search-intent keywords in title, headings, README, and meta descriptions.
8. Promotion: demos, social posts, technical articles, Product Hunt when appropriate.
9. Retention: issue response, monitoring, updates, changelog, examples, integrations.

Do not make drastic pricing changes without explicitly labeling the risk. Prefer fast revenue gains: fill missing Store fields, improve README, add schemas, set PPE correctly, add default test tasks, and promote with one or two high-intent pieces of content.

## Naming And Actor URL

Treat the Actor URL or technical name as a permanent SEO and integration asset.

Rules:

- Choose the technical name early and avoid changing it after publish.
- Changing the Actor URL can reset Google associations and break user API integrations.
- If a URL must change, do it only in the first few days or with user communication.
- Actor name can be changed more freely than URL, but frequent changes can still confuse users.
- Keep the technical name short, ideally under four words.
- Prefer nouns and tool-type keywords: `scraper`, `extractor`, `data`, `api`, `finder`, `downloader`, `checker`.
- Avoid filler adjectives and verbs in the URL such as `best`, `fast`, `light`, `scrape`, `automate`; use those in copy if needed.
- Match Actor name, SEO name, URL, and GitHub repo name when it helps clarity, but use SEO name for keyword expansion.
- Check Store URLs for similar Actors and avoid near-duplicates. Google and users may favor the earlier page.

Naming patterns:

```text
Technical name: <domain>-scraper
Actor name: <Domain> Scraper
SEO name: <Domain> Data Scraper or <Domain> API
GitHub repo: actor-<domain>-scraper
```

For service-specific Actors:

```text
Technical name: <domain>-<service>-scraper
Actor name: <Domain> <Service> Scraper
GitHub repo: actor-<domain>-<service>-scraper
```

For non-scraping Actors, name by function and buyer search intent, not by implementation.

## Monetization Guidance

### Pricing Models

Use the current Apify terminology:

- Pay per event (PPE): users pay for events triggered by Actor code. Best default for revenue scalability, transparent pricing, Store visibility, discounts, and AI/MCP compatibility.
- Pay per usage: users pay platform usage costs only. Good for free/community acquisition or when monetization is not ready.
- Rental: being sunset in 2026. Do not recommend for new Actors unless docs have changed and the user explicitly wants it.

Current documented rental sunset:

- New rental Actors and rental pricing changes stop on April 1, 2026.
- Remaining rental Actors retire on October 1, 2026 and migrate to pay-per-usage.

### PPE Best Practices

Prefer PPE when the Actor creates measurable value per item, per page, per successful enrich, per API call, per exported lead, per document processed, or per workflow completed.

Implementation rules:

- Use official SDK charging when possible: `Actor.charge()` in JavaScript or Python.
- Always inspect `eventChargeLimitReached`. Stop or gracefully finish when the user budget is exhausted.
- For Crawlee, prefer aborting the autoscaled pool gracefully instead of hard `Actor.exit()` when there is post-processing to complete.
- Use idempotency keys when repeated retries could double-charge for the same valuable result.
- Charge for valuable outcomes, not failed attempts.
- Avoid charging tiny noisy internal steps users do not understand.
- If using multiple events, define which one is primary and what each event means in user language.
- Use `apify-default-dataset-item` only when every dataset item maps cleanly to billable value.
- If using multiple datasets, remember only default dataset items trigger the built-in default dataset event.
- Respect `ACTOR_MAX_TOTAL_CHARGE_USD`; the SDK already uses the user limit, but your control flow must still stop wasting compute.

Synthetic start event:

- Recommend enabling `apify-actor-start` for PPE Actors.
- Do not manually charge it in Actor code.
- It helps cover startup overhead while keeping the Actor competitive because Apify covers the first startup window according to current docs.

Pricing formulas:

- Developer profit for monetized usage is generally: `profit = 0.8 * revenue - platform costs`.
- Platform costs can create negative monthly profit if prices are too low or runs are inefficient.
- Use the Actor Analytics tab and representative runs to estimate cost per successful result before setting price.

Pricing selection:

- Start from competitor alternatives outside Apify, then compare similar Apify Store Actors.
- Common Store ranges have often been around low single-digit dollars per 1,000 results, but do not treat this as universal. Match price to value, uniqueness, reliability, and buyer willingness.
- For lead, ecommerce, market intelligence, AI enrichment, or business-critical data, pricing can be higher when the output saves time or generates revenue.
- Include concrete README cost examples: "Scraping 1,000 products usually costs about $X at current settings."
- Offer Bronze/Silver/Gold discounts if the Actor has serious repeat users and margins stay healthy.

Price-change caution:

- Major monetization changes such as increasing prices, adding events, or changing model may require 14-day notice and are limited to once per month.
- Decreases, description changes, and removing events may take effect immediately.
- If recommending a major change, include a user communication note.

## Publication Setup Checklist

In Apify Console, check `Development > My Actors > Actor > Publication`.

### Display Information

Fill every available field:

- Icon: simple, high contrast, recognizable at thumbnail size.
- Actor name: clear, search-intent friendly, usually 40-50 characters where possible.
- Unique name/URL: short, keyword-rich, not deceptive.
- Store description: up to 300 characters, aimed at warm visitors already on Apify.
- SEO name: 40-50 characters, keyword-oriented for Google.
- SEO description: 145-155 characters, aimed at cold visitors from search.
- Categories: choose the strongest maximum allowed, usually no more than 3.
- Hide source files only when needed for business/IP reasons.
- Use custom SEO details when the default description is not search-optimized.
- Actor permissions: use limited permissions whenever the Actor can work with them.
- Maintenance/deprecated flags: never enable unless the Actor is truly not usable.

Description writing rules:

- Say the target/source, output, and buyer value.
- Use keywords naturally: "`<target> scraper`", "`<target> API`", "`<target> data extraction`", "`price monitoring`", "`lead generation`", etc.
- Do not lead with implementation internals.
- Avoid vague claims such as "powerful scraper" unless paired with exact data and use case.
- Keep the regular description human and conversion-focused.
- Keep SEO description dense with search terms and concrete output.

Example regular description pattern:

```text
Extract structured <target> data for <use case>: <key fields>. Supports <important filters>, exports to JSON/CSV/Excel, and handles <main differentiator>.
```

Example SEO description pattern:

```text
Scrape <target> data with a ready API. Extract <fields>, monitor <use case>, and export clean JSON, CSV, or Excel from Apify.
```

### Sample Input

The sample/default input must:

- Run successfully without private credentials when possible.
- Finish quickly enough for Store testing.
- Produce a non-empty default dataset.
- Use low result limits to conserve cost.
- Demonstrate the core value path, not a corner case.
- Include safe defaults, required fields, and realistic example values.

### Schemas

Input schema:

- Use clear titles and descriptions for every user-facing field.
- Use correct editors: `textfield`, `textarea`, `select`, `datepicker`, `number`, `checkbox`, `schemaBased`, etc.
- Use defaults/prefill so new users can run immediately.
- Use enums or suggested values for modes, countries, languages, categories, and sort choices.
- Add validation limits for max pages, max items, date ranges, and URL formats.
- Group advanced controls below simple controls.
- Avoid exposing internal debug flags as primary inputs.

Input schema UX:

- Treat the input schema as the Actor's conversion UI. Many users decide whether to trust and pay from this screen.
- Add a short top-level `description` that reassures the user, names the easiest way to try the Actor, links to a guide when useful, and states any immediate caveat.
- Keep field titles short and noun-like. Put instructions, examples, and caveats in the field `description` tooltip.
- Tooltips should usually start with imperative verbs such as `Enter`, `Add`, `Choose`, or `Use`.
- Use low-cost `prefill` values. High default limits make first runs slow, expensive, and churn-inducing.
- Use prefills to show accepted formats: example URLs, date formats, IDs, keywords, or handles.
- Use `default` placeholder-style values when the user needs to see an example without actually submitting it.
- Word boolean toggles positively and avoid negation traps. A toggle like `Scrape open places only` is clearer than `Skip closed places` when the default matters.
- Use `sectionCaption` to group alternate input modes, filters, output options, and advanced settings.
- Use `sectionDescription` for section-level caveats, pricing implications, or risk notes that must be visible before a user clicks a tooltip.
- Keep technical proxy/browser/debug fields visually secondary and below the main path.
- Use target-site terminology such as `videos`, `tweets`, `listings`, `places`, or `products` instead of generic `results` when it matches user expectations.
- Use emojis only as sparse, consistent visual anchors across schema and README. Never rely on them for critical meaning, and ensure text still works without them.
- If users repeatedly ask obvious questions, make mistakes, or churn after starting, audit input schema before blaming demand or pricing.

Dataset schema:

- Define fields with `title`, `description`, `type`, and `example`.
- Include the fields users actually buy: URL, title/name, price, rating, availability, seller/business, location, date, category, contact/enrichment fields, source, run metadata.
- Add views for the common output use cases: overview, pricing, leads, errors, debug, raw data.
- Include enough field metadata for AI agents and API consumers to understand the output.

Output schema:

- Define output even if it is empty.
- Link default dataset results with `{{links.apiDefaultDatasetUrl}}/items`.
- Link important key-value store collections when used.
- Use output schema and dataset schema together: output schema says where results are; dataset schema says what each item means.

Key-value store schema:

- Add it when the Actor writes files, reports, screenshots, PDFs, media, logs, or grouped artifacts.
- Use prefixes/collections so users see the useful keys first.

Live-view / OpenAPI:

- Add only when the Actor exposes a live web server/API during runs.
- Use OpenAPI v3 so users and agents know how to call the live endpoint.

## README Conversion And SEO Playbook

Treat the README as the Actor landing page, not a developer repo readme.

Hard formatting:

- Do not add an H1; Apify uses Actor name as H1.
- Use H2 for main sections because they become the table of contents.
- Use H3 for subsections.
- Put keywords in H2/H3 where natural.
- Keep the first 25% of the README highly useful because it gets the most attention.
- Include at least 300 words for SEO depth unless the Actor is intentionally tiny.
- Use Markdown tables and JSON examples.
- Embed a YouTube URL on its own line when a demo exists.
- Link images to the Actor or signup page when useful.

Recommended README structure:

```md
## What does <Actor Name> do?
Two or three plain-language sentences. Mention the target site/source, output, and the main API/search-intent keyword.

## Why use <Actor Name>?
Business use cases and pain removed. Use bullets tied to outcomes: monitoring, lead generation, price intelligence, enrichment, automation, research.

## How to use <Actor Name>
1. Open the Actor.
2. Enter <main input>.
3. Set <limit/filter>.
4. Run the Actor.
5. Download JSON, CSV, Excel, or connect via API.

## Input
Table with field, type, required, description, example.

## Output
JSON example and table of fields.

## How much does it cost to scrape <target>?
Explain pricing model and give realistic cost examples.

## Tips for best results
Show how to keep costs low, avoid broad inputs, use filters, set limits, and improve match quality.

## Integrations
API, schedule, webhook, Zapier/Make, Google Sheets, dataset export, MCP/AI agent use.

## Troubleshooting
Common empty result, auth, limit, timeout, or blocked-source cases with exact fixes.

## FAQ
Answer buyer objections and SEO questions.
```

README must answer:

- What exact data can I get?
- How fast and how fresh is it?
- What do I need to input?
- How do I pay and estimate cost?
- What output formats are available?
- Can I schedule it or use it by API?
- What are the common limits?
- Why this Actor over alternatives?
- What happens when one source/platform fails?

SEO workflow:

1. List target search intents: "scrape <site>", "<site> API", "<site> data", "<site> price monitoring", "export <site> to CSV", "best <site> scraper".
2. Choose one primary keyword and 3-6 secondary keywords.
3. Put the primary keyword in SEO name, SEO description, first paragraph, and at least one H2.
4. Use secondary keywords in headings and examples without stuffing.
5. Add a pricing section because cost queries can convert well.
6. Add a comparison/use-case section when competitors or manual workflows exist.

## Quality Score Optimization

Apify quality score affects Store discoverability and recalculates several times per day. Audit each category:

- Reliability: high success rate, stable target handling, automated tests, graceful partial failure, non-empty default dataset.
- Popularity: clear use case, promotion, saves, repeat usage, content links.
- Feedback and community: respond quickly to Issues, improve onboarding, avoid first-run confusion.
- Ease of use: clear inputs, defaults, README, examples, helpful errors.
- Pricing transparency: predictable PPE or clear pay-per-usage explanation, cost examples, discounts where useful.
- Trustworthiness: limited permissions wherever possible.
- History of success: keep Actors maintained and avoid abandoned public Actors.
- Congruency of texts: name, descriptions, README, schemas, and real output must all say the same thing.

If the Console says "Actor strength: Room to grow", prioritize:

1. Missing display fields.
2. Missing icon/categories.
3. Missing custom SEO details.
4. Missing input/schema/sample.
5. Missing dataset/output schemas.
6. Missing README depth.
7. Limited permissions not configured.
8. No automated tests or monitoring.

## Automated Testing And Maintenance

Set up tests before scaling promotion.

Recommended test setup:

- Create 1-5 saved tasks for key scenarios.
- Include one default configuration test.
- Set `maxItems` or equivalent low enough to finish cheaply.
- Use a recurring schedule.
- Review failures weekly.
- Monitor issues and respond promptly.

Apify Store automated QA expectations commonly include:

- Run with default/prefill input.
- Finish with `SUCCEEDED`.
- Produce non-empty default dataset.
- Complete within about 5 minutes unless excluded.

If the Actor needs auth or longer runs, contact Apify support or document the limitation clearly. Do not rely on a broken default input.

Maintenance budget:

- Reserve about 2 hours per week per monetized Actor for issue response, target-site changes, pricing review, docs updates, and test maintenance.
- Before breaking changes, contact Apify/community support if docs require it and communicate to users.
- Keep a changelog or README "What's new" note for meaningful updates.

## Promotion Playbook

High-conversion promotion should show the Actor producing useful output, not just announce it.

Quick wins:

- Share the Actor on personal LinkedIn/X with a 30-90 second demo.
- Tag `@apify` where appropriate.
- Add the Actor to a portfolio/content hub.
- Add it to email signature or freelance profile.
- Ask early users for feedback after successful runs.
- Set up the Apify Store bio under `Settings > Account > Profile` with contact email, website, GitHub, X/LinkedIn/Discord, booking link, newsletter, YouTube/blog, portfolio links, and a short credibility summary.
- Cross-link related Actors from each Actor README because automatic related-Actor recommendations may not cover different categories by the same creator.

Video:

- 5-10 minute tutorial: problem, output preview, configuration, run, results, export/API, pro tips, CTA.
- Short-form video: hook in first 3 seconds, show manual work vs Actor output, captions, portrait format.
- Embed the YouTube tutorial in the README.

Communities:

- Reddit: answer real questions first; use "I built X to solve Y" rather than hard selling.
- Stack Overflow: provide a genuinely helpful answer and mention the Actor as one option only when relevant.
- Quora: 300-500 word practical answers with subheadings.
- Discord/Slack: follow rules, ask for feedback, share working examples.

Content:

- "How I built this" technical post.
- "Best <category> tools" roundup with competitor comparison.
- "<Target> API tutorial" showing Apify API use.
- GitHub examples repo with snippets, integration guides, and Store link.

Product Hunt:

- Best for broad, visual, or productivity-oriented Actors.
- Prepare tagline, screenshots/GIFs, demo video, concise description.
- Launch on a weekday, typically Tuesday-Thursday.
- Build pre-launch momentum.
- Engage in comments all day.
- Keep messaging consistent across Product Hunt, Store, and social posts.

User communication and retention:

- Use `Messaging > Emails > Compose new` to email users of a specific Actor when there is a clear reason.
- Good reasons: new feature, target website change, output/schema change, pricing/payment-model change, deprecation/unpublishing, major issue, fixed outage, webinar, newsletter with multiple useful updates.
- Do not spam. Keep emails concise, friendly, direct, and action-oriented.
- Send a preview to yourself before sending to all users.
- For pricing or breaking changes, send warning and reminder emails with dates, impact, migration steps, and related Actors if applicable.
- For newsletters, bundle 2-3 updates instead of emailing every tiny change.

Issues tab:

- Treat the public Issues tab as support, trust signal, and SEO surface.
- Response time is visible in Actor metrics, so silence damages conversion.
- Respond quickly even when the fix will take time; keep users updated.
- Ask reporters to share the run and exact input; shared runs are private context, not public page content.
- Use screenshots, run links, and exact steps in responses.
- Encourage users to search existing issues before creating duplicates.
- Maintain ready answers for common categories: bug, feature request, question, usage mistake, target-site change, pricing/export confusion.
- Close issues only with a clear resolution or next path.

Affiliate and services revenue:

- Add Apify affiliate links and professional-services referral strategy when the user asks for total Apify revenue, not only Store Actor revenue.
- Affiliate content works best when it demonstrates a real workflow: tutorials, courses, webinars, client recommendations, examples repos, and community answers.
- Track which channels produce referrals and double down on the winners.

Actor bundles:

- Bundles are chains of Actors unified by one use case. They can be valuable when users want a complete workflow and do not want to run multiple Actors manually.
- Bundle positioning must explain the end goal, not just list component Actors.
- Profitability is less predictable because bundles can be top-of-funnel and users may not search for them directly.
- For bundles, use README pricing to explain how component Actor pricing affects the final run cost.
- Do not build a bundle when a single focused Actor with strong search intent would rank and convert better.

## Competitor And Pricing Research

When asked to maximize revenue, inspect competitors instead of guessing:

1. Search Apify Store for target/source keywords.
2. Sort by relevance/popularity where available.
3. Record pricing model, visible price, description, categories, reviews, run stats, last update, output clarity, README structure, and differentiators.
4. Search Google for non-Apify alternatives and SaaS/API pricing.
5. Identify the buyer segment: developer, ops team, ecommerce seller, lead-gen agency, data team, AI workflow builder.
6. Recommend a price anchored to value and margin.
7. Inspect competitor Issues tabs for repeated unresolved pain points. Those are differentiation opportunities.
8. Inspect competitor README first quarter, input complexity, output examples, and pricing explanation. These often explain conversion gaps better than feature lists.
9. Look for spending signals outside Apify: users naming current tools, monthly budgets, paid upgrades, invoices, or complaints about competitor pricing.

Use the Store API if useful:

```bash
curl -sS "https://api.apify.com/v2/store?search=<keyword>&limit=20" | jq '.data.items[] | {name,title,username,description,stats,pricingInfo}'
```

If `pricingInfo` is absent or incomplete, inspect Store pages manually.

## Output Format For User

For a full optimization pass, return:

```text
CURRENT STATE:
- Actor:
- Monetization:
- Missing Store fields:
- Current risks:
- Demand/competition:

REVENUE PRIORITIES:
1. Highest impact now
2. Next
3. Later

PASTE-READY PUBLICATION FIELDS:
- Actor name:
- SEO name:
- Technical name / URL:
- Description:
- SEO description:
- Categories:

README:
<paste-ready README or patch plan>

SCHEMAS:
- Input schema changes:
- Dataset schema:
- Output schema:

MONETIZATION:
- Recommended model:
- Events:
- Primary event:
- Suggested initial price:
- Budget/limit handling:
- Price-change notice if needed:

QUALITY SCORE:
- Reliability:
- Ease of use:
- Pricing transparency:
- Trustworthiness:
- Congruency:

PROMOTION:
- First 7 days:
- First 30 days:
- Issues/email/user-retention:
- Store bio/cross-promotion:

IMPLEMENTATION:
- Files to edit:
- Commands to run:
- Verification proof:
```

For a narrow request, output only the relevant parts, but still preserve concrete paste-ready artifacts.

## Actor-Specific Example: Multi-Platform Ecommerce/Price Scraper

When optimizing an Actor like a multi-platform price scraper, emphasize:

- Buyer value: price intelligence, resale margin analysis, product monitoring, competitor tracking.
- Output fields: product, model, capacity, condition/grade, platform, seller, price, currency, URL, timestamp, match confidence, exclusion reason, availability.
- Differentiators: multi-platform fault isolation, per-platform status, normalized grades, per-source freshness, partial results when one platform fails.
- Pricing event candidates:
  - `result-item`: each normalized listing or price row.
  - `platform-query`: each platform searched for a product.
  - `product-processed`: each input product completed across selected sources.
  - Avoid billing failed platform attempts unless the failed attempt still delivered value.
- README sections:
  - "Scrape product prices across multiple marketplaces"
  - "Compare prices by condition or grade"
  - "Monitor resale margins and market movement"
  - "Export normalized price data to JSON, CSV, or Excel"
- Dataset views:
  - Overview by product/platform.
  - Valid matches.
  - Excluded/low-confidence matches.
  - Platform status and errors.

## Hard Rules

- Do not claim revenue optimization is complete from generic advice. Produce concrete publication fields, README copy, schema recommendations, monetization event design, and verification steps.
- Do not skip market validation when the user is choosing a new Actor or deciding whether an Actor is worth major investment.
- Do not change an established Actor URL lightly; it is both SEO and integration surface.
- Do not make the first-run default expensive or slow.
- Do not bury critical caveats only in README when they belong in input schema descriptions or section descriptions.
- Do not leave Issues tab unanswered; public silence is a conversion and trust problem.
- Do not recommend rental for new Actors unless official docs have changed.
- Do not recommend price increases without checking current monetization-change rules and user communication needs.
- Do not hide platform costs or make pricing hard to predict.
- Do not charge users for failed internal work unless it is explicit, valuable, and documented.
- Do not add broad features when quick publication fixes will unlock the immediate Store strength/revenue gain.
- Do not publish private business details, credentials, target account names, tokens, or internal run data in public README copy.
- Do not overclaim "AI/MCP ready" unless output schema and field metadata are present enough for agents to consume the Actor.
- Do not call an Actor reliable until default input, non-empty dataset, and at least one real run or test task prove it.
