# Hotel Booking Analysis: Reducing Cancellations and Increasing Revenue

An end-to-end exploratory data analysis of 119,390 hotel bookings (City Hotel and Resort Hotel, Portugal, 2015-2017) to find out who cancels, when demand peaks, and what the hotel can do to protect revenue.

## Business Problem

A canceled room-night that cannot be resold is lost income, and overbooking to make up for it risks walking guests. This project answers four questions:

1. How many bookings are canceled, and who cancels?
2. When are demand and prices highest?
3. Which channels and customer types are most valuable?
4. What should the hotel do to cut cancellations and raise revenue?

## Key Findings

- **About 28% of bookings are canceled** after cleaning (City Hotel about 30%, Resort Hotel about 24%). Canceled bookings carry roughly **one third of total booked revenue**.
- **Lead time is the strongest signal.** Bookings made within 7 days cancel 8.5% of the time, while bookings made 6 to 12 months ahead cancel about 40%.
- **Online travel agents** bring the most volume but cancel about **35.5%**. Direct and Offline agent bookings cancel about 15%, and Corporate about 12%.
- **Repeat guests cancel about 8%**, versus 28% for new guests. Cancellations also fall as guests make more special requests.
- **The Resort Hotel is highly seasonal**: average daily rate is about 50 in January and about 184 in August. The City Hotel is much steadier.
- **The cancellation rate rose every year**: about 21% (2015), 27% (2016), 32% (2017).

## Recommendations

1. Require deposits, or offer discounted non-refundable rates, for bookings made more than 90 days ahead.
2. Use stricter cancellation windows or controlled overbooking for online travel agent bookings on peak dates.
3. Grow direct bookings with perks such as free breakfast or late checkout.
4. Invest in loyalty, since repeat guests are about 3.5 times less likely to cancel.
5. Prompt for special requests at booking to increase guest commitment.
6. Price dynamically: raise Resort rates from June to September and run winter promotions.
7. Send confirmation reminders to the Portuguese market, which cancels most.
8. Investigate the rising cancellation trend, for example whether channel mix is driving it.

## Data Cleaning Summary

| Issue | Action |
|---|---|
| 31,994 duplicate rows | Removed |
| Missing `children`, `country`, `agent` | Filled with 0, "Unknown" and 0 |
| `company` column about 94% empty | Dropped |
| Zero-guest and zero-night bookings | Removed |
| Zero or negative `adr` and one extreme outlier | Excluded |
| `meal = Undefined` | Treated as no meal package |

Result: 119,390 rows reduced to **86,637 clean bookings**.

**Data quirks flagged in the analysis:** parking and room-change fields look like outcome-related data (recorded at or after check-in) and should not be used as predictors, and the Non Refund deposit group shows an unexpectedly high cancellation rate that is probably a data-entry artifact.

## Tools

Python, pandas, NumPy, matplotlib, seaborn, Jupyter Notebook

## Repository Contents

| File | Description |
|---|---|
| `hotel_booking_analysis.ipynb` | Full analysis: cleaning, charts, insights, recommendations |
| `hotel_bookings_2.csv` | Dataset |
| `Hotel_Booking_Analysis_Report.pdf` | Written summary report |

## How to Run

```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook hotel_booking_analysis.ipynb
```

Keep `hotel_bookings_2.csv` in the same folder as the notebook.

## Limitations and Next Steps

- The data covers only two hotels in Portugal, so results may not generalise.
- Removing duplicates is a judgment call and changes the headline cancellation rate (37% before, about 28% after).
- 2015 and 2017 are partial years, so year-on-year comparisons are approximate.
- **Next step:** build a classification model (logistic regression or random forest) to predict cancellations, excluding the outcome-related fields noted above.

## Data Source

Hotel Booking Demand dataset, by Nuno Antonio, Ana de Almeida and Luis Nunes (published in *Data in Brief*, 2019), also available on Kaggle.

## Author

**Shrey Shah**: B.Tech Computer Science student, interested in data analytics and healthcare analytics.
[LinkedIn](https://www.linkedin.com/) | [GitHub](https://github.com/)
