# A/B Test Analysis: Ad vs. PSA Conversion Impact

## Business Question
Marketing ran an A/B test showing users either a real ad or a public service
announcement (PSA, the control). This analysis asks: does the ad actually lift
conversion, is that lift big enough to matter commercially, and are there
segments worth targeting if we scale it up?

## Dataset
- Source: (https://www.kaggle.com/code/adhamtarek147/a-b-testing-analysis/notebook)
- ~588,000 users, 7 columns (test group, conversion outcome, ads seen, day/hour
  of exposure)

## Methods
- Two-proportion z-test to compare conversion rates between ad and PSA groups,
  with a 95% confidence interval on the lift itself (not just a p-value)
- One-way ANOVA + eta-squared to check whether day and hour of exposure
  meaningfully explain variation in conversion
- Binned analysis of ad frequency vs. conversion rate to check for diminishing
  (or confounded) returns

## Key Findings
- Ads lift conversion by 0.77 percentage points over PSA (2.55% vs. 1.79%,
  95% CI 0.60–0.94pp) — statistically robust and not just a large-sample
  artifact
- Day and hour of exposure are statistically significant but explain a
  negligible share of variance (eta-squared ≈ 0.0007) — not a reliable basis
  for targeting
- Conversion keeps rising with ad frequency rather than plateauing, which
  looks more like a confound (engaged users see more ads) than a true
  frequency effect
- Cost-per-impression isn't in the dataset, so a full ROI/scale-or-not call
  needs that input from marketing

## Tools
Python, pandas, scipy, statsmodels, seaborn/matplotlib
