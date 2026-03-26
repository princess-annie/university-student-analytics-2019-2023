## Project Title
Nigerian University Student Performance & Enrollment Analytics (2019–2023)

## Business Objective
To analyze student academic performance, enrollment trends, and financial patterns across university departments ,
identifying at-risk students, revenue drivers, geographic distribution, and the relationship between attendance and academic outcomes.

## Dataset Overview
The dataset covers 420 student records from a Nigerian university across 5 years (2019–2023), 
including GPA, attendance, graduation status, tuition revenue, department, enrollment year, and 
state of origin across 4 departments and 5 Nigerian states. The dataset was self-generated with chatgpt for analytical purposes.

## Tools Used
1. Power BI
2. DAX; 
* graduation Rate
<img width="1190" height="141" alt="image" src="https://github.com/user-attachments/assets/740d189f-7559-4ffa-9eac-5e190ca66ade" />

* Underperforming Rate 
<img width="1199" height="256" alt="image" src="https://github.com/user-attachments/assets/a9c8a40e-1607-4702-b352-bb943b06e947" />

* High Performance Rate
<img width="1194" height="174" alt="image" src="https://github.com/user-attachments/assets/844427a0-da2b-4f13-b9c6-39531b3b0ab2" />

* Tuition Revenue 
<img width="844" height="45" alt="image" src="https://github.com/user-attachments/assets/7e03189d-d762-4793-96ca-95c4355d9927" />

3. Data Cleaning:
* Set and Correct data types
* Created a new student_id column because there were a lot of data quality issue; i used Power Query
* Worked on Inconsitent Capitalization, Inconsistent Formatting and Trailing Spaces
* For Enrollment Date Column, it came in diff format, use a dax query to change it to one format
 d = Text.Trim([Enrollment_Date]),
    cleaned = Text.Replace(d, "/", "-"),
    parsed = 
        try Date.FromText(cleaned, [Format="yyyy-MM-dd"]) otherwise
        try Date.FromText(cleaned, [Format="dd-MM-yyyy"]) otherwise
        try Date.FromText(cleaned, [Format="MM-dd-yyyy"]) otherwise
        try Date.FromText(cleaned, [Format="M-d-yyyy"]) otherwise
        try Date.FromText(cleaned, [Format="d-M-yyyy"]) otherwise
        null
in
    parsed),
* The Graduation Date was Inconsistent, used the below query to change it
Date.Addyears([Enrollment_Date], [Duration])
if [Graduation_Date] = null
then Date.Addyears([Enrollment_Date], [Duration])
else [Graduation_Date]
* Replace Values in the GPA column from 35-3.5

## Key KPIs
1. EXECUTIVE OVERVIEW
* total students, 
* average gpa across all dept,
* average attendance across all students, 
* graduation rate of students, 
* tuition revenue

2. ACADEMIC ANALYSIS
* average gpa across all dept, 
* average attendance across all students, 
* graduation rate of students, 
* underperforming rate and high performance rate

3. ENROLLMENT ANALYSIS
* tuition revenue
* total students
* avg duration study

## Key Insights
* Student Performance Overview 
- This page provides a high-level snapshot of the university's performance from 2019 to 2023. 
- As of the latest data (2023), the university has enrolled 420 students, generated $310.5M in tuition revenue, 
- maintained a 3.34 average GPA, and recorded an 83.1% average attendance rate across all departments. 
- Use the Year and Department filters to explore how these numbers shift across different periods.
<img width="1250" height="712" alt="image" src="https://github.com/user-attachments/assets/260dfc98-993d-4648-a4ad-49999c5c9ea6" />

* In the Course of analysis, Graduation Rate shows that;
- The 2019 and 2020 cohorts show 100% graduation rates because those students had completed their programs by the reporting period. 
- The graduation rate decline from 2021 onward dropping to 62.2% in 2021, 11.8% in 2022, and 0% in 2023  which does not indicate academic failure. 
- It reflects the fact that students enrolled in 2021, 2022, and 2023 are still actively studying and have not yet reached their graduation year.

* Academic Analysis Insights examines how students are performing academically across all 4 departments. 
- As of 2023, the university maintains a 3.34 average GPA and 83.1% attendance rate, with a high performance rate of 65.2% and 
- a persistent underperforming rate of 20.5%. 
- Use the filters to identify which departments are excelling and which ones need attention."
<img width="1244" height="703" alt="image" src="https://github.com/user-attachments/assets/519ff227-7ac7-47f2-ba15-5175b78aa4f4" />

* Enrollment Analysis
- Tracks where students are coming from and what courses are generating the most revenue.
- As of 2023, 420 students have enrolled from 5 Nigerian states over the 5-year period, with an average study duration of 4 years 
- and total tuition revenue of $310.5M. Use the Year and Department filters to see how enrollment patterns and revenue shift over time."
<img width="1244" height="707" alt="image" src="https://github.com/user-attachments/assets/532b970c-fbb7-4ed0-bbc9-3ff90ccbb59d" />

## Recommendations
- Introduce academic intervention programs to address the consistent 20% underperforming rate across all departments.
- Investigate the 2022 enrollment decline 
- Increase Health Sciences intake since it generates the highest revenue per student
and expanding it is the most efficient revenue growth strategy.

## Note: 
- This is a fictional dataset created for portfolio purposes. 
- Some anomalies observed: such as the 100% underperforming rate in Computer Science (2022) 
are a reflection of the data generation process and may not represent real-world scenarios.


## Detailed Analysis
[Read the full article on Medium](https://medium.com/@princessjames563/introduction-every-university-tracks-enrollment-numbers-a28c36884fbd)
