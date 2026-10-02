# What Drives Views on Branded Short-Form Content?

An analysis of 54 of my own sponsored brand videos (October 2024 to September 2026), testing with data the patterns I had only noticed by instinct as a content creator.

## Background

As a content creator in Nepal, I have created sponsored content for more than 40 brands across Instagram, Facebook, and TikTok. Over time, I formed beliefs about what works: humor-first videos outperform direct promotions, and videos under one minute perform best. Yet my longest video, a 2:38 video for inDrive's "Dream It, Do It" campaign, reached 859,000 organic views. I wanted evidence instead of instinct.

## Questions

1. Do videos that open with humor get more views than videos that open directly with the promotion?
2. Is there a trade-off between reach (views) and brand exposure (whether viewers stay until the brand appears)?
3. Do longer videos perform worse?
4. Does the timing of the promotion matter?

## Data

- 54 sponsored videos posted between October 2024 and September 2026
- Organic views combined across Instagram, Facebook, and TikTok; for videos where brands also ran paid ads, only organic views were included
- Variables: views, video length, second at which the promotion starts, opening style (humor, direct, or other), average watch time (Instagram), and posting date
- Opening styles: 45 humor, 6 direct, 3 other (emotional or plain voiceover)

## Methods

- Medians instead of means, because a few viral videos make the distribution highly skewed
- Mann-Whitney U test to compare humor and direct openings
- Spearman correlations for length and promotion timing
- Comparison of average watch time against promotion start time to estimate brand exposure
- Multiple regression (OLS with robust HC3 standard errors): `log10(views) ~ length + promotion position + direct opening + paid ads + posting order`
- Robustness checks removing the most-viewed video and videos with paid ads

## Key Findings

**1. Humor-first openings reached about three times more viewers.** Humor videos had a median of 64,100 views versus 22,208 for direct openings (Mann-Whitney p = 0.0001). Within a single brand, inDrive's humor videos (151,517 and 73,000 views) also far outperformed its direct videos (about 20,000 each).

**2. There is a trade-off between reach and brand exposure.** In all 6 direct videos, the average viewer was still watching when the promotion began. In only 1 of 45 humor videos did the average viewer reach the promotion. Humor maximizes reach, but many viewers likely leave before the brand appears.

**3. Longer videos did not perform worse, contrary to my expectation.** Videos over 60 seconds had a median of 71,970 views versus 48,258 for shorter ones (Spearman rho = 0.30, p = 0.03).

**4. Promotion timing showed a weak, uncertain pattern.** Among humor videos, a later promotion was weakly associated with more views (rho = 0.25, p = 0.10).

**5. The regression could not separate opening style from promotion timing,** because direct openings and early promotions occur together. However, the estimated effect of a direct opening stayed consistently negative (about −38% to −47%) across all robustness checks.

![Views by opening style](figures/02_opening_style.png)
![Reach vs. brand exposure](figures/03_reach_vs_exposure.png)
![Views vs. video length](figures/04_length_vs_views.png)

## What This Means

The data confirmed one of my beliefs (humor works), challenged another (shorter is better), and revealed something I had not considered: the most-viewed content may not deliver the most brand exposure. A natural next step is testing a hybrid approach, such as a subtle early brand cue within a humor-first story.

## Limitations

- Small, observational sample (n = 54): these are patterns, not proof of cause
- Only 6 direct videos, three of them for one brand
- Average watch time does not show how many individual viewers reached the promotion
- Videos also differed in brand, topic, campaign size, and timing

## Next Step

A controlled experiment: publishing versions of the same content that differ in only one factor, such as promotion at 5 seconds versus 30 seconds, to isolate its effect.

## How to Run

Open `content_performance_analysis.ipynb` in Google Colab, upload the data file, and run all cells.

## Tools

Python (pandas, NumPy, SciPy, statsmodels, Matplotlib), Google Colab
