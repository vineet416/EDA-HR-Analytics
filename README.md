# HR Analytics – Employee Engagement EDA
 
Exploratory data analysis of an HR dataset covering 311 employees (active and terminated).
The notebook cleans the data and explores salary, performance, engagement, satisfaction, absences, recruitment and attrition.
The goal is to give HR a quick, visual view of workforce patterns and where to focus attention.

## Project Files

| File | Description |
|---|---|
| `EDA-HR-Analytics.ipynb` | Main notebook: cleaning, EDA, 7 visualizations, and a short "Internal Assignment" section |
| `HRDataset_v14.csv` | Source data: 311 rows × 36 columns, one row per employee |
| `README.md` | Project documentation (this file) |

## Dataset

| Field(s) | Description |
|---|---|
| `Employee_Name`, `EmpID` | Employee name and unique ID (311 unique IDs) |
| `GenderID`/`Sex`, `MarriedID`/`MaritalDesc`, `MaritalStatusID` | Gender and marital status, as codes and labels |
| `CitizenDesc`, `HispanicLatino`, `RaceDesc`, `DOB`, `State`, `Zip` | Demographics and location |
| `DeptID`/`Department`, `PositionID`/`Position` | Department (6) and job position (31 after trimming spaces) |
| `ManagerName`, `ManagerID` | Direct manager (21 names) |
| `Salary` | Annual salary (45,046 – 250,000) |
| `DateofHire`, `DateofTermination`, `Termd`, `TermReason` | Hire/exit dates (2006–2018), termination flag and reason |
| `EmpStatusID`, `EmploymentStatus` | Active, Voluntarily Terminated, Terminated for Cause |
| `PerfScoreID`, `PerformanceScore`, `LastPerformanceReview_Date` | Exceeds / Fully Meets / Needs Improvement / PIP |
| `EngagementSurvey`, `EmpSatisfaction` | Engagement score (1.12–5.0) and satisfaction rating (1–5) |
| `SpecialProjectsCount`, `DaysLateLast30`, `Absences` | Special projects (0–8), days late (0–6), absences (1–20) |
| `RecruitmentSource`, `FromDiversityJobFairID` | Hiring channel (9 sources) and diversity job fair flag |

## Approach

1. **Understand the data** – inspected shape, columns, dtypes (`df.shape`, `info()`, `dtypes`).
2. **Clean** – checked nulls (`DateofTermination` 207, `ManagerID` 8), filled them with `"0"`, checked for duplicates (none).
3. **Explore** – top salaries, PIP list, absences, marital status, special projects, recruitment sources.
4. **Visualize** – salary extremes, recruitment sources, performance counts, satisfaction, salary by department, engagement by position, marital status by gender.
5. **Group analysis** – engagement, absences and salary by department; terminations by position, reason and department; hire dates by manager.

## Key Insights

All figures were recomputed directly from `HRDataset_v14.csv`.

| Area | Finding |
|---|---|
| Attrition | 104 of 311 employees (33.4%) have left: 88 voluntary, 16 for cause |
| Where attrition sits | Production has 209 staff and 83 exits (79.8% of all exits); its exit rate is 39.7% vs 16.1% in Sales and 20.0% in IT/IS |
| Exit reasons | Another position (20), unhappy (14), more money (11), career change (9) |
| Salary | Median 62,810; mean 69,021. Top earner is the President & CEO (250,000), then the CIO (220,450) |
| Salary by department | Median is lowest in Production (59,472) and highest in IT/IS (92,328) and Software Engineering (95,660) |
| Gender pay | Median salary F 62,066 vs M 63,353 (about 2% lower), not adjusted for role |
| Performance | Fully Meets 243 (78.1%), Exceeds 37, Needs Improvement 18, PIP 13 (8 Production, 4 Sales, 1 IT/IS) |
| Engagement | Mean 4.11. Sales is lowest (3.82); Admin 4.39, IT/IS 4.15, Production 4.13 |
| Satisfaction | Most common rating is 3 (108 employees); 192 (61.7%) rate 4–5; only 11 rate 1–2 |
| Special projects | 70 employees have at least one; 241 have none |
| Absences | 3,184 total (average 10.2 each); Production accounts for 2,120 |
| Recruitment | Indeed (87), LinkedIn (76) and Google Search (49) supply 68% of hires |
| Extra checks (not in the notebook) | Exit rate by source: Google Search 61% (30/49) vs Employee Referral 16% (5/31); engagement correlates with `DaysLateLast30` (r = −0.59) and tracks performance (PIP 2.22 vs Exceeds 4.48) |

## Tech Stack

- **Python 3** in a Jupyter Notebook (ipykernel)
- **pandas, NumPy** – loading, cleaning, `groupby`/`agg`, `value_counts`
- **Matplotlib, Seaborn** – bar, horizontal bar, line, stem, box and count plots

## How to Use

1. Clone or download this folder and keep the CSV next to the notebook (it is read by relative path).
2. Install dependencies: `pip install pandas numpy seaborn matplotlib jupyter`
3. Start Jupyter: `jupyter notebook EDA-HR-Analytics.ipynb`
4. Run all cells. Saved outputs are also visible without running.
