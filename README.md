# A/B Testing: MScFE Applicants

A randomized controlled experiment for an online data science education platform. About a quarter of applicants create an account but never take the admissions quiz. The experiment tests whether sending those applicants an encouragement email makes them more likely to complete the quiz.

All applicant data is synthetic.

## The experiment

- **Question:** does receiving an email make an applicant more likely to complete the admissions quiz?
- **Design:** each day, applicants who signed up the previous day and have not taken the quiz are randomly assigned to a treatment group (gets the email) or a control group (gets nothing), then monitored for quiz completion.
- **Analysis:** a 2x2 table of group against complete/incomplete, plus a power analysis to work out how many observations and how many days are needed to detect a small effect.

## Layout

| Path | Purpose |
|---|---|
| `database.py` | `MongoRepository`: connects to MongoDB (`wqu-abtest` database, `ds-applicants` collection) and returns applicant data as DataFrames (nationality counts, ages, education level) |
| `business.py` | `GraphBuilder` (choropleth map, age and education charts) and `StatsBuilder` (observations needed, experiment simulation) |
| `display.py` | Dash app components: demo graphs, group-size and cumulative-distribution displays, results |
| `notebook.ipynb` | The analysis, end to end |
| `Data/MScFE-data.csv` | Synthetic applicant records |
| `2023-09-0X_ab-test.csv` | Daily experiment files: emails tagged `ab-test` |
| `notes.txt`, `projectNotes.rtf` | Working notes: concepts, goals and decisions for each lesson |

## Setup

Requires Python 3, a local MongoDB on `localhost:27017` loaded with the applicant data, and these packages: `pandas`, `numpy`, `pymongo`, `plotly`, `scipy`, `statsmodels`, `country_converter`, `dash`, and `teaching_tools` (the WorldQuant University course helper that provides the `Experiment` class). There is no requirements file yet.

Start with `notebook.ipynb`; the `.py` modules are imported by the notebook and the Dash app.
