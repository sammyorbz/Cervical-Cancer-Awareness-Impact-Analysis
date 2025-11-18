# 📊 Cervical Cancer Awareness Study — Pre & Post Intervention Analysis

![Project Banner](images/cervical.jpg)

---

### 🧠 Overview  
This project analyzes the **impact of a health education intervention** on cervical cancer awareness among female senior high school students.  
Data were collected using **pre-test** and **post-test** questionnaires, three months apart.  
The study evaluates how students’ knowledge changed across four awareness domains and an overall awareness score.

---

## 🎯 Objectives
- To clean, organize, and analyze pre-test and post-test data from a cervical cancer awareness campaign.  
- To compare domain-wise awareness levels before and after intervention.  
- To statistically determine if the differences in awareness were **significant**.  
- To visualize and report findings for presentation and Power BI dashboard.

---

## 🧩 Step 1: Load and Explore the Data

**Goal:** Import Excel data and check sheet contents.

```python
import pandas as pd

file_path = "Cervical Cancer Data.xlsx"
xls = pd.ExcelFile(file_path)
xls.sheet_names

Results

['CC Study', 'Pretest', 'Post Test']


✅ We identified that:

CC Study = Raw merged data.

Pretest and Post Test = Cleaned, separated datasets for before and after intervention.


🧼 Step 2: Data Cleaning and Verification

Goal: Check dataset sizes and consistency.

pre_df.shape, post_df.shape

Results:

Pre-test: (1107, 34)
Post-test: (1276, 34)

✅ Observation:

Post-test had 169 more students than the pre-test.

This could slightly affect overall averages — but since paired analysis uses the same 1107 participants, the comparison remains valid.


👩‍🏫 Step 3: Demographic Summary

Goal: Understand participant distribution by age and class.

pre_df[['age', 'SHS Class']].describe()
pre_df['SHS Class'].value_counts()

Results:

Mean age = 16.1 years

Most represented: SHS 3 (43%), followed by SHS 2 (39%), SHS 1 (18%)

✅ All participants were female senior high school students, ages 14–18.


🧮 Step 4: Awareness Domain Means (Pre vs Post)

Goal: Compute mean awareness scores for each domain.

| Domain      | Pre Mean  | Post Mean | Mean Difference |
| ----------- | --------- | --------- | --------------- |
| Domain I    | 1.98      | 2.92      | +0.94           |
| Domain II   | 2.48      | 2.83      | +0.35           |
| Domain III  | 2.50      | 3.09      | +0.60           |
| Domain IV   | 3.48      | 3.95      | +0.47           |
| **Overall** | **10.44** | **12.80** | **+2.35**       |

✅ Awareness improved across all domains, especially Domain I (Knowledge of Cervical Cancer).


📈 Step 5: Statistical Significance (Paired t-test)

Goal: Test if post-test improvement is statistically significant.

| Domain      | Mean Difference | t-statistic | p-value      | Significance  |
| ----------- | --------------- | ----------- | ------------ | ------------- |
| Domain I    | 0.99            | 29.17       | 3.07e-139    | ✅ Significant |
| Domain II   | 0.36            | 7.17        | 1.40e-12     | ✅ Significant |
| Domain III  | 0.63            | 14.54       | 5.82e-44     | ✅ Significant |
| Domain IV   | 0.49            | 10.03       | 9.73e-23     | ✅ Significant |
| **Overall** | **2.47**        | **22.00**   | **2.79e-89** | ✅ Significant |

✅ Interpretation:
All domains show highly significant improvement (p < 0.05) — confirming that the intervention had a real, measurable impact.


📊 Step 6: Visualization — Mean Awareness (Pre vs Post)

Goal: Show mean score improvements visually.

import seaborn as sns
import matplotlib.pyplot as plt

sns.barplot(x='Domain', y='Mean', hue='Test Type', data=summary_df)
plt.title("Mean Awareness Scores (Pre-test vs Post-test)")
plt.show()

The chart clearly shows post-test means higher than pre-test across all domains.


🧩 Step 7: Awareness Adequacy (Categorical Distribution)

Goal: Compare how many students achieved “Adequate” vs “Inadequate” awareness per domain.

| Domain      | Pre-test Adequate (%) | Post-test Adequate (%) |
| ----------- | --------------------- | ---------------------- |
| Domain I    | 73.0%                 | 94.4%                  |
| Domain II   | 78.0%                 | 87.1%                  |
| Domain III  | 81.8%                 | 89.3%                  |
| Domain IV   | 82.9%                 | 91.0%                  |
| **Overall** | **79.1%**             | **92.3%**              |

✅ Clear upward shift — post-intervention, more students moved from Inadequate → Adequate.


🧮 Step 8: Domain Variable Mapping

Each domain represents grouped knowledge questions:

| Domain     | Theme                | Example Variables                                       |
| ---------- | -------------------- | ------------------------------------------------------- |
| Domain I   | General Awareness    | `CC Cause`, `CC Curable`, `CC Begins In Cervix`         |
| Domain II  | Symptoms Knowledge   | `Vaginal Bleeding`, `Frequent Urination`, `Painful Sex` |
| Domain III | Risk Factors         | `Sex At Young Age`, `Many Sexual Partners`, `Smoking`   |
| Domain IV  | Prevention & Control | `HPV Immunization`, `Regular Screening`, `Exercise`     |

✅ These mappings guided the analysis of which aspects of knowledge improved most.


💡 Step 9: Power BI Dashboard Integration

Goal: Visualize the entire study interactively.

Steps:

Export pretest and posttest datasets as .csv files.

Load both into Power BI Desktop.

Create a Clustered Bar Chart:

Axis → Domain

Legend → Test Type (Pre vs Post)

Values → Mean Score

Add visuals:

Domain-wise Adequacy Pie Charts

KPI cards for Mean Improvement

Filter slicers (Age, Class, Domain)

Dashboard Title:

🎓 Cervical Cancer Awareness Improvement Analysis (Pre vs Post Evaluation)

Description (for Power BI title page):

This analysis evaluates the impact of a health education intervention on cervical cancer awareness among senior high school girls.
Pre- and post-test data were compared across key awareness domains to measure knowledge improvement.
Results show a significant increase in overall awareness and adequacy across all domains after the intervention.


🧾 Step 10: Key Insights & Conclusion

✅ Significant awareness improvement across all domains (p < 0.05).
✅ Domain I (basic knowledge) had the highest gain (+0.94).
✅ Over 92% of students achieved adequate awareness post-intervention.
✅ Educational programs are effective tools for improving cervical cancer awareness among adolescent females.


🧰 Tools Used

| Category             | Tools                         |
| -------------------- | ----------------------------- |
| Data Cleaning        | Python (Pandas)               |
| Statistical Analysis | SciPy                         |
| Visualization        | Matplotlib, Seaborn, Power BI |
| Documentation        | Markdown, GitHub              |








