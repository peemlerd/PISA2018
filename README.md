# Project description 

This data analysis project is done on PISA 2018 data on Thai students' education achievement during my internship at Thailand Development Research Institute (TDRI) from late Dec 2019 to early Jan 2020.

# Background

Thai students are not doing well academically. According to the [World Bank](https://www.worldbank.org/en/country/thailand/publication/wanted---a-quality-education-for-all-in-thailand), a significant proportion of 15-year-old Thai students are functionally illiterate, especially those in the rural areas. Some researchers  have attributed Thailand's lagging performance in education to its overemphasis on [rote memorisation](https://oxfordbusinessgroup.com/overview/learning-curve-despite-premium-placed-learning-sector-has-struggled-show-positive-results-0), [shortage of education staff](http://uis.unesco.org/sites/default/files/documents/secondary-teachers-in-thailand-secondary-teacher-policy-research-in-asia-2011-en.pdf), and so on. Because there are many stakeholders in any education system (e.g. policymakers, teachers, students, parents, etc.), it is difficult to attribute what causes the successes or failures of the system. The problem with Thai education is exacerbated by [Thailand's lack of data availability](https://www.bangkokpost.com/opinion/opinion/1219025/open-data-policy-the-key-to-success): the absence of data makes it difficult for policymakers to empirically evaluate the effectiveness of their policies. 

# Project's goal 
To empircally understand factors affecting Thai students' education performance. 

# Why use PISA 2018 data? 

First, PISA is one of the few open-source empirical data about Thai students' education achievement.  <br />
Second, PISA collects a detailed information on each student, be it their parents' background, socioeconomic status, school condition, class size, and so on. The richness of PISA dataset allows researchers to analyze the relationship between education performance and factors that may influence it.  <br />
Third, unlike those in previous years, participants in PISA 2018 were asked to answer questionnaire on their attitudes towards education (e.g. growth mindset, expected highest level of education) and their emotion state. Because the impact of mindset on education has received a lot of attention from researchers on Thai education (e.g. [Tayjasanant et al.](https://www.researchgate.net/publication/311605841_Thai_EFL_teachers_and_learners'_beliefs_and_readiness_for_autonomous_learning)), PISA 2018 data on each student's attitude may contribute to the conversation. 

# Work process

1.) **Loaded the data**: I loaded the data from PISA website on the education achievement of Thai students in 2018. <br /> 

2.) **Background survey**: I skimmed through PISA methodology (e.g. how the test was administered, how PISA imputes missing data) and the codebook on what each column stands for to understand the format of the data and how to analyze them. 

3.) **Literature search**: I researched previous literatures on PISA results. These literatures included [the PISA 2018 executive summary](https://www.oecd.org/pisa/PISA%202018%20Insights%20and%20Interpretations%20FINAL%20PDF.pdf), [PISA's comparison of Thailand and other countries](http://www.compareyourcountry.org/pisa/country/THA), and papers about Thai education that analyze PISA data. The excerpt of each paper is as provided below: 

- [TDRI Quarterly Review — Quality Education for All](https://tdri.or.th/wp-content/uploads/2012/09/t5j2012.pdf): The authors of this paper advocated for an increased accountability system for Thai schools through initiatives such as mandatory standardized tests, promoting school autonomy, and so on. 
- [Pre-primary education and long-term education performance: Evidence from Programme for International Student Assessment (PISA) Thailand](https://journals.sagepub.com/doi/abs/10.1177/1476718X15616834?journalCode=ecra) by Piriya Pholphirul. Mr. Pholphirul analyzes PISA data and concludes that pre-primary education positively correlates with cognitive skills, especially among low-income students.
- [School autonomy and accountability in Thailand: Does the gap between policy intent and implementation matter?](https://link.springer.com/article/10.1007/s11125-015-9368-8) by Patrinos et. al. The article asserts that schools with more autonomy tend to perform better in PISA reading tests. 

Moreover, I discussed current education initiatives at TDRI with my colleagues and my research supervisor at the institution to identify how PISA 2018 data might inform those initiatives. Based on this research, I discovered that many papers focus on the effect of school accountability, school autonomy, and socioeconomic status on education achievement. Given that PISA 2018 tests include questions on students' attitude and experience on education, both of which are not extensively studied in papers I came across, I decided to analyze the relationship between atttitude and education performance. 

4.) **Cleaning data**: Once I decided upon which project to undertake, I looked through the questionnaire every participant of PISA 2018 must answer and selected questions pertaining to attitude. Afterwards, I checked the responses each student provided and eliminated rows corresponding to students who provided too many 'No Responses' and coluumns corresponding to questions that are not properly answered (e.g. questions that were likely to be misinterpreted or had too many 'No Responses'). 

5.) **Imputed missing data and convert the ordinal data to a numerical scale**: Some students only had one 'No Response' out of the many answers they provided. Therefore, I did not remove those students but imputed the 'No Response' cells based on the most frequent answer that appeared on that column. Afterwards, because the answers to those questions are mostly in the ordinal scale (e.g. never >> always, strongly disagree >> strongly agree), I converted the responses to an 1-4 scale. 

6.) **Run the regression model with all variables**: This step provides a rough picture of which factors potentially correlate strongly with education achievement. 

7.) **Fine-tune the regression model by choosing variables with high coefficients and R-squared values** I would group variables in Step 6 into different categories (e.g. fear of failure, growth mindset), ran regression with variables in each category, and only chose variables with high R-squared, low interaction, and high coefficients. 

8.) **Interpret the final regression model and summarize its results**: The section below describes the result of this project.

# Results
<br /> In this project, I created two regression models: <br />  <br />
**Project 1**: Regressing on education performance (Y) using responses to attitude questions as predictor variables (X). 
<br />
**Project 2**: Regressing on education performance (Y) using responses to summary statistics predictor variables (X). 
<br />. The summary statistics are Warm-Likelihood Estimates (WLE) calculated by PISA based on each student's response to every question on the survey. 
**Note**: The model calculates and regresses on education performance for three separate subjects — mathematics, science, and reading. 


For **Project 1**, I found out that the *positive* factors that strongly correlate with education achievements are presence of extrinsic motivations, fear of failure, and the sense of pride when students master or successfully complete a task. On the other hand, *negative* factors include fixed mindset, isolation from peers, and enjoyment from competition. These attitude factors explain 25% of the variance in mathematics score of Thai students in the PISA 2018 dataset. 

For **Project 2**, the PISA 2018 data corroborated many previous studies on what works in Thai schools. The result is: <br />

1.) Factors that *positively* correlate with education achievement: enjoyment in reading, deriving enjoyment from mastering a task, fear of failure, sense of belonging, socioeconomic status, presence of school activitoes.
<br />

2.) Factors that *negatively* correlate with education achievement: perceived difficulty in reading, discrimination, shortage of education staff, high student-to-teacher ratio, presence of behaviors that hinder learning, and attending private schools. 

These WLE factors explain 51% of the variance in reading score of Thai students in the PISA 2018 dataset.

These factors show similar trends when I applied regression on other subjects. 

# Future Goals 

1.) **Fixing the reversed causality problem.** Currently, it remains unclear whether positive and negative factors influence education achievement, vice versa, or there are other latent factors. For instance, a student might not perform well academically because he has a fixed mindset, or not performing well academically may cause him to adopt a fixed mindset.    <br />
2.) **Create an index that reflects the mobility of a student.** If a student has high socioeconomic (escs) status, it is likely that her academic performance will be better than that of her less well-off peers. However, it is interesting to see which characteristics among the high-mobility students -- coming from the bottom quartile on escs but scoring at the top quartile in different subjects). Figuring out factors correlated with high mobility helps stakeholders in education design an intervention to improve the quality of education more effectively.  

# About the author
This project is done by Peem Lerdputtipongporn, Swarthmore College Class of 2021. As a Mathematics and Computer Science major, Peem is interested in using statistics and computation to make a positive impact to society. His area of interest includes education, economic development, and finance. For Summer 2020, he is looking for an internship/fellowship in Data Science for Social Good. 

# Acknowledgement
I undertook this project during my internship at Thailand Development Research Institute (TDRI). I wish to extend my gratitude to my colleagues at TDRI who provided me with guidance and emotional support, both of which play a crucial role in the completion of this project. 
