# SpaceX Falcon 9 First Stage Landing Prediction

Applied Data Science Capstone — IBM Data Science Professional Certificate.

## Problem

SpaceX advertises Falcon 9 launches at roughly $62M, against upwards of $165M
for other providers. Much of that difference comes from SpaceX's ability to
recover and reuse the first stage. So if we can predict whether the first stage
will land, we can estimate the cost of a launch — which is exactly what a
competitor bidding against SpaceX would want to know.

This project builds that prediction from historical launch data.

## Repository layout

```
├── notebooks/
│   ├── 01-data-collection-api.ipynb        # SpaceX REST API extraction
│   ├── 02-data-collection-webscraping.ipynb # Wikipedia launch records
│   ├── 03-data-wrangling.ipynb             # cleaning, Class label
│   ├── 04-eda-visualization.ipynb          # charts + feature engineering
│   ├── 05-eda-sql.ipynb                    # SQL analysis (SQLite)
│   ├── 06-interactive-map-folium.ipynb     # geospatial analysis
│   ├── 07-dashboard-plotly-dash.py         # interactive dashboard
│   └── 08-predictive-analysis.ipynb        # classification models
├── figures/                                 # exported charts & screenshots
├── presentation/                            # final report (PDF)
└── data/                                    # local datasets (gitignored)
```

## Method

**Collection.** Launch records pulled from the SpaceX v4 REST API and
supplemented by scraping Wikipedia's Falcon 9 launch history table.

**Wrangling.** Filtered to Falcon 9, handled missing `LandingPad` values,
and derived a binary `Class` label from the `Outcome` column — 1 where the
booster landed, 0 otherwise.

**EDA.** Explored the relationship between landing success and flight number,
payload mass, launch site, and orbit type, both visually (seaborn) and with SQL.

**Geospatial.** Mapped launch sites with Folium and measured their distance to
coastline, railway, highway, and nearest city.

**Modelling.** Four classifiers — logistic regression, SVM, decision tree, and
KNN — each tuned with `GridSearchCV` at 10-fold cross-validation, then compared
on a held-out test set.

## Results

Filled in once the notebooks have been run end to end.

| Model | CV accuracy | Test accuracy |
|---|---|---|
| Logistic Regression | | |
| SVM | | |
| Decision Tree | | |
| KNN | | |

## Running these notebooks

The notebooks were originally written for the Skills Network JupyterLite
environment, which provides `piplite` and a browser `fetch`. They have been
adapted to run in standard Jupyter:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn folium dash plotly
jupyter lab
```

Run them in numerical order. Notebooks 04 onward read their datasets straight
from the course's public S3 bucket, so no local data files are required.

## Dataset

Course-provided extracts of SpaceX public launch data, hosted by IBM Skills
Network. Original source: the SpaceX REST API (`api.spacexdata.com/v4`) and
Wikipedia.
