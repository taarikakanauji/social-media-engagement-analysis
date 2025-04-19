# Social Media Engagement Analysis - Power BI Report 

![Power BI Home](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/Power%20BI-HOME.jpg)

## Problem Statement

Stakeholders across various departments lack a centralized, data-driven view to effectively monitor and analyze social media engagement across different platforms, audience segments, content types, and interaction metrics. This gap makes it challenging to identify underperforming campaigns, assess engagement performance, and make informed decisions based on key indicators such as total posts, likes, comments, audience demographics, and platform-specific performance. There is a need for an interactive dashboard that provides actionable insights.

This dashboard helps stakeholders track and analyze social media engagement based on platform (Facebook, Twitter, Instagram), audience segment (age, gender), content type (text, image, video), and engagement metrics (likes, comments, shares). It delivers data-driven insights to uncover trends, improve campaign strategies, optimize content planning, and maximize reach and impact. The dashboard is designed for key stakeholders:

- Social Media Managers & Digital Strategists

- Marketing & Content Teams

- Analytics & Insights Teams

- Campaign Owners

# Objective

`Centralize engagement data across platforms`
Create unified and platform specific dashboards to view and monitor engagement on Facebook, Twitter, and Instagram.

`Identify underperforming platforms using key metrics`
Analyze likes, comments, and shares to uncover gaps and improve future strategies to capture more audience.

`Segment audience insights for better targeting`
Break down engagement by age, gender, and region to analyze how each type of audience is interacting with each of the platform.

`Optimize content strategy based on performance`
Compare engagement across text, image, and video formats to prioritize high-performing content types.

`Enable data-driven decisions for greater impact`
Provide stakeholders with actionable insights to boost reach, engagement, and improve platform performance.

## Key Questions

    Q : How does engagement differ across content types like text, image, and video?

    Q : What are the key demographics (age and gender) engaging with our posts on each platform?

    Q : Which platforms (Facebook, Twitter, Instagram) drive the most interactions?

    Q : What patterns or trends can be observed in likes, comments, and shares over time?

    Q : Are there specific regions where engagement is low but audience size is high?

    Q : Which regions show the highest and lowest levels of engagement across platforms?

    Q : Are there any specific days of the week when the engagement is higher or lower than usual?

    Q : What are the target engagement numbers in terms of likes, shares and comments and if they are achieved or not? 

## Steps followed 

As a Business Analyst for a prominent digital brand, I was tasked with developing an interactive engagement dashboard to help stakeholders monitor audience interaction trends, content performance, and overall activity across various platforms. The goal was to provide actionable insights to improve social media strategy, optimize content delivery across platforms and formats, and enhance audience satisfaction and engagement. Below, I explain my step-by-step approach to designing this dashboard in Power BI:


- Step 1 : Load data into Power BI Desktop. The dataset is a csv file.

- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.

- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".

- Step 4 : After a thorough review and cleanup, we now have a data which contains no errors or empty values across columns — indicating a high-quality dataset ready for transformation and visualization.

- Step 5 : In the report view, under the view tab, default theme was selected.

- Step 6 : Creating KPI Cards for Key Metrics - To provide stakeholders with a clear summary, I created four KPI cards displaying high-level engagement indicators as shown below. These KPIs offer a real-time snapshot of audience interaction and help in making data-driven decisions quickly and effectively.

        Total Posts – Number of social media posts published.
        Measure Used: Total Posts = COUNT('Dataset'[Post_ID])

        Total Likes – Total number of likes received on all posts.
        Measure Used: Total likes = SUM('Dataset'[Likes])

        Total Comments – Total number of user comments.
        Measure Used: Total likes = SUM('Dataset'[Comments])

        Total Shares – Total number of times content was shared.
        Measure Used: SUM('Dataset'[Shares])

        MoM Engagement % Measure:
        MoM Engagement % = CALCULATE(DIVIDE(([Engagement Current Month (MTD)] - [Engagement Past Month (INPERIOD)]),[Engagement Past Month (INPERIOD)]))

        Engagement Measure:
        Engagements = [Total likes] + [Total Shares] +[Total Comments]

        Engagement Past Month Measure:
        Engagement Past Month (INPERIOD) = CALCULATE([Engagements], DATESINPERIOD( 'Date Table (DAX)'[Date], EOMONTH(MAX('Date Table (DAX)'[Date]), -1), -1, MONTH))

        Engagement Current Month Measure:
        Engagement Current Month (MTD) =CALCULATE([Engagements],DATESMTD( 'Date Table(DAX)'[Date]))

        Impressions Measure:
        Impressions = SUM('Dataset'[Impressions])

   I formatted these cards with currency symbols to make trends easily understandable. These KPIs help executives quickly assess fundamental performance without diving into granular data.

  ![KPIs](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/kpi.jpg)
           
- Step 7 : Representing the engagements by gender – I added a pie chart to illustrate how audience interactions are distributed across different gender identities.

        Fields Used:

        Legend: Gender (Female, Male, Other)

        Values: Total Engagements (Total of Likes, Comments and Shares)

   The chart revealed that the highest engagement came from users identifying as “Other” (35.1%, 637K), followed by Male (33.13%, 601K) and Female (31.77%, 576K). The data suggests a fairly balanced interaction across all gender groups, with a slightly higher contribution from users categorized as “Other.”

  ![Gender Engagement](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/gender-engage.jpg)

- Step 8 : Representing the engagements by age group and platform – I used a stacked area chart to display how user engagements vary across different age groups and social media platforms. 

        Fields used:

        Legend: Platform (Facebook, Instagram, Twitter)

        Y-Axis: Total Engagement (Total of Likes, Comments and Shares)

        X-axis: Age Group (Young Adult, Adult, Senior)

   The chart revealed that Adults and Seniors each contributed equal engagements, with Facebook driving the highest volume in both groups. Among Young Adults, overall engagement was notably lower at 0.41M, with equal engagement on Facebook and Twitter (0.14M each), and slightly less on Instagram (0.13M). This suggests Facebook remains the dominant platform for older demographics, while younger audiences show balanced interaction across all platforms but at reduced levels.

  ![Age Platform Distribution](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/age-platform.jpg)

- Step 9 : Representing daily engagement trends – I added a column chart to visualize user engagement levels across each day of the week, highlighting patterns in platform usage over time. 

        Fields used:

        Y-Axis: Total Engagement (Total of Likes, Comments and Shares)

        X-Axis: Day of week (Mon, Tue, Wed, Thurs, Fri, Sat, Sun)

  The chart revealed that Thursday and Sunday recorded the highest engagement levels, suggesting users are most active toward the end of the workweek and on weekends. Friday saw the lowest engagement, while Monday to Wednesday showed equal levels of engagement. This insight helps identify optimal days for content release and user interaction strategies.

  ![Daily Engagement](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/daily-engage.jpg)

- Step 10 : Total Engagement split by content type - This donut chart is pretty simple and highlights the percentage division of total engagement depending on the type of media content. 

        Fields used:

        Legend: Content Type (Text, Image, Video, Carousel)

        Values: Total Engagement (Total of Likes, Comments and Shares)

  The distribution is roughly the same across different types, with Text and Image being slightly higher than the other two. The Video and Carousel types stood equal in terms of their engagement.

  ![Engagement Split by Type](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/split-type.jpg)

- Step 11 : Total Engagement & Impressions split by content type - This bar chart simply highlights the number of impressions and engagements for all the platforms.

        Fields used:

        Legend: Content Type (Engagements, Impressions)

        Y-Axis: Platform (Facebook, Instagram, Twitter)

        X-Axis: Parameter for Total Impressions and Total Engagements

      Dynamic Title are displayed on click of Impression and Engagement Button using Modeling tab > New parameter, Which gave me new parameter table.  

  The impressions numbers don't differ significantly between the different platforms, with Facebook leading the way, followed by Instagram and then lastly Twitter.     

  ![Impressions](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/impression.jpg) 


- Step 11 : Adding Filters to the Dashboard – To improve the user experience, I added five slicers that allow users to filter the data according to their specific needs. These slicers are conveniently accessible via a filter icon located at the top of the dashboard.

  Configuring Slicers for Interactive Filtering – To enable users to interactively explore the report and focus on particular areas of interest, I set up slicers that dynamically filter the entire dashboard. These filters help users drill down into key dimensions for more targeted analysis.

  I added slicers for:

  `Gender (Male, Female, Other)`

  `Content Type (Text, Image, Video, Carousel)`

  `Platform (Facebook, Instagram, Twitter)`

  `Country`

  `Date`

  I chose dropdown-style slicers for a clean interface, ensuring they influence all report visuals. This allows business teams to filter data—for example, comparing the transaction frequencies in terms of various scenarios. 

  ![Power BI Filter](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/Power%20BI-FILTER.jpg)

- Step 12 : To improve the usability and interactivity of the Power BI report, I added a Reset Filters icon that enables users to easily clear all slicer selections and revert the report to its original default state. This functionality boosts user confidence by ensuring that any filter changes can be effortlessly undone, providing greater flexibility and ease of use.

First, I inserted a reset or refresh icon using the Insert > Image option and positioned it to the left of the filter icon for better visibility and accessibility.

Next, I manually cleared all slicer selections, including Gender, Content Type, Platform, Country and Date.

Finally, I activated the Action feature on the reset icon by setting the Type to Bookmark and linking it to the Clear all Filters bookmark. This setup ensures that clicking the icon resets all slicers and filters to their default (unselected) state.
  
# **Instagram Analysis**  

The dashboard for Instagram, as the name suggests, specifically highlights the crucial numbers, trends and targets related to Instagram. The key purpose of this dashboard is to understand what's working and what's not for Instagram, and use that information to make pivotal decisions that will further the growth of the platform in the future.

  ![Instagram Analysis](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/Insta-report.jpg)


- The `Engagements` bar chart shows the overall engagement during all the months. The fluctuation is fairly stable and indicates that the usage remains at a certain level throughout the year. The last quarter does go a little higher compared to other quarters.

- The `Monthly Engagement` line chart shows the comparison between current month and previous month engagement. This indicator is necessary to monitor the engagement in a relatively short timeline of the past, which if needs correction, can be taken action upon immediately.

- The `Daily Engagement by Gender` highlights how each of the genders are engaging with the platform on a day to day basis. The distribution is not extremely polarized towards one or the other gender, but the Other gender seems to be a bit higher compared to Male and Female.

- Having `Targets for Shares, Comments and Likes` are important as well, since they give a direction to the platform. The numbers ultimately indicate if the platform is catering to its user's demands or not. Another important aspect of these targets is new user acquisition and existing user retention. 


**Insights**

584K total engagements in the past month, indicating solid audience interaction.

Shares exceeded targets, suggesting highly sharable content

Comments and likes fell short to achieve target, signaling a need for more viral-worthy content.

**Challenges**

Low likes compared to targets may reflect content lacking relatability or incentive to spread

Heavy like focus risks superficial engagement without meaningful conversations.

**Recommendations**

Analyze competitors’ high-share posts for inspiration

Add share prompts (e.g., "Tag a friend")

Leverage comment-friendly formats (polls, Q&As) to sustain discussion momentum.

# **Facebook Analysis**  

  ![Facebook Analysis](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/Facebook-report.jpg)

Facebook Analysis is designed to track, measure, and interpret engagement trends across content, demographics, and regions. By evaluating performance metrics—such as MoM growth, audience behavior, and geographic distribution—it identifies strengths, weaknesses, and opportunities to refine content strategy, improve audience targeting, and maximize reach.

**Insights**

Engagements reached 638K (past month) with 24.4% MoM increase, indicating accelerating performance.

Current and past monthly engagement, shows fluctuations suggest inconsistency.

**Challenges**

Drops from 67K → 35K in current and past month comparison, reveal unstable performance.

In quarter engagement, sudden drop in Q3. 

**Recommendations**

High-performing months to replicate successful planning

Benchmark against competitors in these areas to identify gaps

# **Twitter Analysis**  

The dashboard for Twitter is designed to spotlight essential metrics, trends, and targets specific to Twitter performance. Its primary goal is to analyze what drives engagement and what doesn’t, helping stakeholders make informed decisions to boost platform growth.

  ![Twitter Analysis](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/Twitter-report.jpg)

It features visual insights through graphs showing:

`Overall engagement` during the months of the year. This is a fundamental statistic that stake holders would want to know.

`Engagement by date and content type` indicates which content type was used how many times in a given day. This may reveal some interesting patterns in how users engage with the platform in regards to special days such as festivals, world events, etc.

`Monthly engagement comparison (current vs. previous month)` shows the month over month comparision of the engagement on the platform. This is essential in monitoring short term engagement and rapidly tackle any sudden dips in the engagement.

`Engagement trends by day of the week` highlights the trend observed during days of the week.

**Insights**

Palau leads with 8,806 engagements (5,127 likes, 2,644 shares, 1,035 comments)

Total engagements reached 592K in the past month with a 3.4% month-over-month (MoM) increase, showing steady growth

Likes dominate engagement types across top countries

**Challenges**

Sep Current month shows significant drop compared to past month’s

High like counts but relatively lower shares/comments suggest content may not be compelling enough to drive broader conversations or viral sharing.

**Recommendations**

Analyze top-performing posts in Palau/Jordan to replicate successful planning

Investigate cultural/local trends in top countries to tailor content

Conduct competitor analysis in high-potential regions like Jordan where engagement is strong but may have untapped potential

Run campaigns specifically targeting comment generation (Q&A sessions, controversial topics)

# Snapshot of Report (Power BI Service)

  ![Power Service Full](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/Power-Service-full.jpg)

# Report Snapshot (Power BI DESKTOP)

  ![Power BI Full Report](https://github.com/taarikakanauji/social-media-engagement-analysis/raw/main/images/Power-BI-full.jpg)

# **Project Resources**  

### **Detailed Report (PDF)**  
[Insights of Social Media Engagement Analysis](https://github.com/taarikakanauji/social-media-engagement-analysis/blob/main/Social%20Media%20Engagement%20Analysis.pdf)  

### **Power BI Desktop Demo**  
[Power BI Demo (MKV)](https://github.com/taarikakanauji/social-media-engagement-analysis/blob/main/Power-BI-Demo.mkv)  

### **Power BI Service Demo**  
[Power BI Service Demo (MKV)](https://github.com/taarikakanauji/social-media-engagement-analysis/blob/main/Power-Service-Demo.mkv)  

### **PBIP Files**  
- **Report:** [Report Files](https://github.com/taarikakanauji/social-media-engagement-analysis/tree/main/Social%20Media%20Enagagement%20Report.Report)  
- **Semantic Model:** [Semantic Model Files](https://github.com/taarikakanauji/social-media-engagement-analysis/tree/main/Social%20Media%20Enagagement%20Report.SemanticModel)  
- **Project File:** [Social Media Engagement Analysis PBIP](https://github.com/taarikakanauji/social-media-engagement-analysis/blob/main/Social%20Media%20Enagagement%20Report.pbip)  
- **Gitignore:** [.gitignore](https://github.com/taarikakanauji/social-media-engagement-analysis/blob/main/.gitignore)  

### **Project README (Setup Guide)**  
[README.md](https://github.com/taarikakanauji/social-media-engagement-analysis/blob/main/README.md)  

# Conclusion

This dashboard empowers stakeholders to:

- Identify novel patterns and trends amongst the different platforms and the engagement on them all.
- Identify the potential future opportunities related to each age group and target them with respect to their preferred particular platforms.
- Develop a plan to introduce new features that would appeal to the existing users as well as bring new users to the platforms.

By leveraging these insights, the resources can be allocated more effectively to high-performing segments, underperforming areas can be identified and addressed proactively, and strategic decisions can be made with greater confidence. This data-driven approach empowers stakeholders to optimize features on platforms, boost engagements, and enhance user satisfaction. Ultimately, the dashboard serves as a centralized tool for continuous engagement monitoring and improvement. It enables the organization to stay agile and competitive in a dynamic social media landscape.  


