# Jumping-the-Gun
https://www.ukonward.com/wp-admin/post.php?post=36371&amp;action=edit&amp;classic-editor
Fair Share Renewables Index. The index is composed of three variables with values ranging from 0 to 1, so that each English constituency is relatively ranked. The three variables are:

Inverted onshore wind block support. This measures support for allowing onshore wind to be built, with a higher value (maximum 1) equating to greater levels of support
Land feasible km2. This indicates the remaining available feasible land for onshore wind and solar generation projects by constituency, a higher value (maximum 1) indicating a relatively higher availability of land
MW accepted since 1990. This indicates the relative share of renewables taken on since 1990 by each constituency with 1 indicating the highest share. 

These three variables are then averaged to create an overall score across which the components can be assessed to determine the likelihood of future development. 

In the overall Index an area hypothetically scoring one would therefore be the area with the highest support for renewables, the highest feasible land, and the highest MW accepted; An area hypothetically scoring 0 would have the lowest value across these three variables.

Methodology Overview
This methodology note clarifies the approach used to identify and analyse areas in England that are likely to bear the brunt of the 2030 renewables transition. The goal of this analysis is to assess both the distribution of feasible land for onshore renewable generation and the existing scale of renewable energy projects at the constituency level, using min-max scaling to create an index. This index enables a comparison of constituencies to determine which areas are most likely to experience future development pressures and how this may align with political opposition.
Data Sources
1. Friends of the Earth – Feasible Land for Onshore Renewable Generation
The dataset from Friends of the Earth, in collaboration with the Environmental Intelligence Centre at the University of Exeter, identifies areas suitable for onshore wind and solar generation in England. Researchers employed a conservative approach, excluding sensitive areas such as:
National Parks and Areas of Outstanding Natural Beauty (AONBs)
High-grade agricultural land
Small developments
Heritage sites
The analysis revealed a total of 219,800 hectares suitable for onshore wind and 295,000 hectares for solar, which could generate an estimated 130,421 GWh of solar power and 95,542 GWh of wind power—far exceeding the current 17,063 GWh combined. This dataset provides the feasible land area (km²) for renewable development by constituency.
2. Renewable Energy Planning Database (REPD)
The Renewable Energy Planning Database (Q2 2024 update) tracks the progress of renewable energy projects from planning application to operation. For this analysis, the dataset was filtered to include only operational onshore wind and ground-mounted solar projects in England. The total installed capacity (MW) of these projects was summed by constituency to indicate the scale of renewables already adopted.
Process
Mapping Feasible Land and Installed Capacity


The Friends of the Earth data was imported into QGIS as a CSV and joined to a base map of England’s 2024 parliamentary constituencies using British National Grid coordinates (EPSG: 27700). Feasible land was mapped in km² for each constituency.
The REPD data was also converted into a CSV, filtered for operational onshore wind and ground-mounted solar projects, and joined to the same base map using British National Grid coordinates. The resulting dataset provided the total installed capacity (MW) of operational projects per constituency between 1990 and Q2 2024.
This combined dataset was then exported from QGIS as a CSV table, containing each English constituency along with its party affiliation, feasible land for renewables (km²), and installed renewable capacity (MW).
Formulating the Index
 In Excel, the dataset was prepared for analysis. Several constituencies had no feasible land or operational renewable projects, resulting in zero values. To avoid issues with log transformation, small scale factors were added:


Feasible land: 0.00007
Installed capacity (MW): 0.00002
These adjustments ensured that log transformations could be applied without distorting the distribution. A logarithmic transformation was then performed to normalise the data and address skewness in the distribution.

 Following the transformation, each variable was min-max scaled. This method was chosen over z-score standardisation to preserve the relative distances between values, enabling a more intuitive interpretation of which constituencies had the most feasible land and installed capacity relative to others. The resulting index allowed for the identification of constituencies that:


Have significant feasible land and are therefore likely to be targeted for future renewable developments.
Already host substantial renewable capacity, providing insight into constituencies that may experience further development pressures.
Judgement of Variables


Feasible Land (km²): This variable reflects the potential for future renewable projects. Constituencies with a high value are more likely to face additional development.
Installed Capacity (MW): This represents the level of renewable infrastructure already in place. Constituencies with a high value are understood to have already experienced significant development.
Political Context and Polling
To gauge potential opposition to future developments, onshore wind was used as a proxy for local attitudes towards renewable energy infrastructure. Unlike solar, onshore wind developments were subject to a de facto ban until recently, making opposition to it a more reliable indicator of aversion to new energy infrastructure. Constituencies with significant installed capacity but high aversion to onshore wind reflect areas where political resistance may be stronger, despite their existing contribution to the renewable transition.
Conclusion
This methodology provides a structured approach to understanding the spatial distribution of renewable energy potential and existing capacity across English constituencies. The resulting index highlights areas with the greatest capacity for future development and informs the political risk of opposition, offering valuable insights for policymakers navigating the 2030 renewables transition. 

Constituency polling by Survation: https://www.survation.com/polling-in-every-constituency-in-britain-shows-strong-support-for-building-wind-farms-to-drive-down-consumer-bills/
Friends of the Earth Feasible Land data: https://policy.friendsoftheearth.uk/download/full-data-analysis-englands-onshore-renewable-energy-potential
Renewable Energy planning Database: https://www.gov.uk/government/publications/renewable-energy-planning-database-monthly-extract
