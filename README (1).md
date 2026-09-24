# Student Performance Analytics and Prediction

**AICTE | IBM SkillsBuild Data Analytics with AI Internship 2026** (BharatCares in association with AICTE)

**Author:** Yuvraj Sharadchandra Patil, B.E. Computer Engineering, Sinhgad College of Engineering, Vadgaon, Pune (SPPU)
**GitHub:** [yuvraj-sp](https://github.com/yuvraj-sp)

---

## Project Description

Schools usually find out that a student is struggling only after the final results are published, which is too late to help. This project analyses a secondary-school student dataset to:

1. Understand overall performance through **KPIs and trends**
2. Find the **drivers** behind better and worse final grades
3. Identify **at-risk students** (those likely to fail)
4. Build a **machine learning model** that predicts the final grade
5. Turn the findings into **recommended actions** for teachers

The project follows the business-intelligence flow: *Data → KPIs → Trends → Drivers → Risks and Opportunities → Actions.*

## Dataset

- **Name:** Student Performance Data Set (Portuguese language course, `student-por.csv`)
- **Size:** 649 students, 33 columns (demographic, family, social, school and lifestyle attributes, plus grades G1, G2, G3)
- **Target:** `G3`, the final grade (0 to 20). A student passes with `G3 >= 10`
- **Dataset link (Kaggle):** https://www.kaggle.com/datasets/larsen0966/student-performance-data-set
- **Original source (UCI):** https://archive.ics.uci.edu/dataset/320/student+performance
- **Citation:** P. Cortez and A. Silva (2008). *Using Data Mining to Predict Secondary School Student Performance.* Proceedings of the 5th FUture BUsiness TEChnology Conference (FUBUTEC 2008), pp. 5-12.

## Technologies Used

| Tool | Purpose |
|---|---|
| Python 3 | Programming language |
| Pandas, NumPy | Data loading, cleaning, calculations |
| Matplotlib, Seaborn | Visualisation |
| Scikit-learn | Machine learning models and evaluation |
| Jupyter Notebook | Development environment |

## Repository Contents

| File | Description |
|---|---|
| `Yuvraj_StudentPerformance.ipynb` | Complete project code (single notebook) |
| `requirements.txt` | Python libraries needed to run the project |
| `Yuvraj_Patil_ProjectReport.docx` | Full project report with charts and results |
| `README.md` | This file |
| `student-por.csv` | Dataset (also downloadable from the Kaggle link above) |

## Setup and Run Instructions

1. **Get the files.** Download or clone this repository. Make sure `student-por.csv` is in the same folder as the notebook. If it is missing, download it from the Kaggle link above.
2. **Create a virtual environment (recommended).**
   ```bash
   python -m venv .venv
   .venv\Scripts\activate        # Windows
   source .venv/bin/activate     # macOS / Linux
   ```
3. **Install the requirements.**
   ```bash
   pip install -r requirements.txt
   ```
4. **Open the notebook** in Jupyter or VS Code:
   ```bash
   jupyter notebook Yuvraj_StudentPerformance.ipynb
   ```
5. **Run all cells** (Run All). The notebook prints the tables and results, and saves 9 charts into a `charts/` folder it creates automatically. Running takes under a minute.

## What the Notebook Does

1. Loads the data (auto-detects the file separator)
2. Checks quality: no missing values, no duplicate rows
3. Creates helper columns: pass/fail flag, at-risk flag, absence bands
4. Calculates 5 KPIs
5. Plots grade trends and the factors that influence grades
6. Analyses which student groups are most at risk
7. Trains and compares Linear Regression and Random Forest, with and without the earlier grades G1 and G2
8. Prints insights, risks, opportunities and recommended actions

## Key Results

**KPIs**

| KPI | Value |
|---|---|
| Total students | 649 |
| Average final grade (out of 20) | 11.91 |
| Pass rate | 84.6% |
| At-risk students (G3 below 10) | 15.4% |
| Average absences | 3.7 |

**Risks found**

- Students with past failures fail **49.0%** of the time, versus 9.3% for those without
- Students studying under 2 hours a week fail **23.6%**, versus 6.8% for those studying 5+ hours
- Students with more than 10 absences fail **24.5%**, versus 13.8% for those with 5 or fewer
- Students who do not plan higher education fail **47.8%**, versus 11.6% for those who do

**Model performance (20% test set)**

| Setup | Model | MAE | RMSE | R² |
|---|---|---|---|---|
| A. With G1 and G2 | Linear Regression | 0.765 | 1.215 | 0.849 |
| A. With G1 and G2 | Random Forest | 0.751 | 1.247 | 0.841 |
| B. Without G1 and G2 | Linear Regression | 2.156 | 2.862 | 0.160 |
| B. Without G1 and G2 | Random Forest | 2.057 | 2.820 | 0.185 |

5-fold cross-validation of the full model gave a mean R² of **0.78**.

**Takeaway:** Final grades are predicted well once the first two period grades are known (average error about 0.77 grade points). Without them, prediction is weak, so the early-warning model works as a screening aid and not as a replacement for teacher judgement.

## Recommended Actions

1. **Early-warning programme:** flag students with past failures or low study time in the first weeks of the year
2. **Attendance monitoring:** start a parent and teacher conversation at about 10 absences
3. **Targeted tutoring:** extra classes for students with past failures, the highest-risk group
4. **Motivation and career counselling:** support students who do not plan higher education
5. **Use G1 and G2 checkpoints:** intervene right after the first period grade

## Limitations

- Small dataset (649 students from two Portuguese schools), so results may not generalise elsewhere
- Correlation is not causation
- The early-warning model has limited accuracy

## Future Work

- Add the Mathematics course dataset and compare subjects
- Try gradient boosting and model tuning
- Build a pass/fail classification model
- Create an interactive dashboard for teachers
