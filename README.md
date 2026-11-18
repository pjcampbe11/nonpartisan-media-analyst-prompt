Daily Media Brief

A prompt that turns any web-enabled LLM into a nonpartisan media analyst. You run it once a day. It finds the top stories, pulls coverage from outlets across the political spectrum, sets a factual baseline from primary sources, and shows where each outlet's reporting departs from it.

You get two things out of one read: what actually happened today, and how the media covered it.

Why

Most people get the news from one or two outlets, and every outlet makes choices about what to cover, what to leave out, and how to frame it. Comparing coverage by hand across a dozen sources every day isn't realistic. This prompt does the comparison for you and keeps the output short enough to read in about five minutes.

What it does
Finds the stories. Picks the 8–10 biggest stories by how widely they're being covered, not by what any one side is pushing.
Pulls coverage across the spectrum. Checks outlets in six buckets: Far Left, Left, Center, Right, Far Right, and Independent/Other. Each bucket gets its own searches so one side doesn't crowd out the other.
Sets a baseline. Lists only facts confirmed by primary sources (court filings, official statements, government data, on-record quotes, unedited video) or agreed on by every bucket.
Checks each outlet against the baseline. Looks for omission, framing, named logical fallacies, factual errors, and story placement.
Flags incentives. For outlets that stray far from the baseline, gives a one-line read on the likely reason: audience, ownership, access, politics, or clicks. This is labeled as analysis, not fact.
Checks itself. Before writing the output, the model confirms it held left and right to the same standard and that every serious flag has a source behind it.
Flag labels

The prompt doesn't let the model call something deliberate spin without evidence. Every flag uses one of three labels:

Label	Meaning
FACT ERROR	Verifiably false against primary sources
SPIN	Evidence of deliberate distortion: a refused correction, the same distortion repeated across days, a claim contradicted by documents the outlet had, or a clear financial or political tie. The evidence must be stated.
SLANT	A framing or emphasis choice that isn't provably intentional

When the model isn't sure, it uses SLANT.

Outlet buckets
Bucket	Examples
Far Left	Jacobin, Mother Jones, The Intercept, Democracy Now
Left	CNN, MSNBC, NYT, Washington Post, The Guardian, HuffPost, Vox
Center	AP, Reuters, BBC, NPR, The Hill, Axios, Bloomberg, WSJ (news)
Right	Fox News, NY Post, Washington Examiner, National Review, WSJ (opinion)
Far Right	Breitbart, Daily Wire, The Federalist, Newsmax, OAN, Gateway Pundit
Independent/Other	The Free Press, Semafor, Al Jazeera, Substack journalists, major podcasters

Bias ratings come from AllSides, Ad Fontes Media, or Media Bias/Fact Check. The model names which one it used and flags outlets the raters disagree on. Edit the list in prompt.txt to add or remove outlets.

How to use it
Open any LLM chat that can browse the live web.
Paste in the full contents of prompt.txt.
Send it.

Evening runs (US Central) work best, after the day's coverage has settled.

Works with: ChatGPT, Claude, Gemini, Grok, Perplexity, or any model that can search the web. The prompt doesn't name any tools, so it isn't tied to one vendor.

If the model can't browse, it's told to say so and stop instead of making up headlines. You can paste in articles or links yourself and it will work from those.

Output format
# Daily Media Brief: [Date]

## 1. [Neutral headline]
What happened:  one paragraph, baseline facts only
Coverage:       one line per bucket, outlet → angle
Biggest delta:  where coverage splits hardest
Flags:          [FACT ERROR / SPIN / SLANT] Outlet: issue
Ignored by:     outlets that skipped it

...repeat per story...

## Outlet Scorecard: Today
| Outlet | Bias rating | Stories covered | FACT ERROR | SPIN | SLANT | Note |

## Day in One Paragraph
## Sources

Every flag comes with a short quote (15 words or fewer) and a link, so you can check it yourself.

Running it on a schedule

The prompt is self-contained, so it can run unattended. Some options:

A scheduled task in your LLM app, if it supports one
A cron job that calls a model API with web search turned on and emails or saves the result
A daily reminder to paste it in by hand
Limitations
Output depends on the model's search. If a model can't reach an outlet (paywalls, blocked sites), that outlet gets skipped. The self-check step asks the model to say when its search coverage was thin.
Headline-level flags are weaker than article-level ones. Models sometimes judge a story from its headline or snippet. Treat those flags as leads to check, not conclusions.
Bias ratings aren't neutral facts. AllSides, Ad Fontes, and MBFC each have their own method and critics. Using more than one helps.
"Silence" isn't always a choice. An outlet may have covered a story in a place the model didn't find.
The model has its own bias. The equal-standard self-check reduces it but doesn't remove it. Running the same day through two different models and comparing the results is a good check.
Customizing

Everything is plain text in prompt.txt. Common edits:

Number of stories: change "8–10" in Step 1
Topic focus: add a line to Step 1, such as "Prioritize tech and AI policy stories"
Region: swap the outlet list for non-US outlets
Length: change "readable in about 5 minutes" in the output section
Files
File	Purpose
prompt.txt	The prompt. Paste this into your LLM.
README.md	This file
License

MIT. Use it, fork it, change it.
