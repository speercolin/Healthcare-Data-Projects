# Humana Healthcare Data Analytics Dashboard

### Dashboard Link : https://app.powerbi.com/links/CnkmGLrVMD?ctid=88d59d7d-aecb-41b2-90c5-55595de02536&pbi_source=linkShare

## Problem Statement

This dashboard aims to provide an interactive and visual representation of Humana's market share across Florida's counties. By leveraging geographic data, the dashboard will display an intuitive map where stakeholders can explore Humana's presence and market penetration within each county. This tool will support strategic decision-making by highlighting areas with high and low market share, enabling data-driven insights for targeted growth, competitive analysis, and resource allocation. The dashboard will serve as a critical asset for visualizing market dynamics and identifying potential opportunities for Humana's expansion within Florida.

### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is an Excel file.
- Step 2 : Open power query editor & merge the "County" and "State" columns to create a new "County Name" column.
- Step 3 : Create a custom column titled "Market Share" using the formula below.

        = [Count]/[MMA Total]

- Step 4 : Close and apply power query.
- Step 5 : Build the Filled Map visualization and drag County Name to the Location data field.
- Step 6 : Drag Market Share to the Tooltips data field and change the Data type to Decimal number and the Format to Percentage.
- Step 7 : Adjust the Tooltip for Market Share to show the Sum.
- Step 8 : Drag Sum of Count & Sum of Population to the Tooltips data field as well.
- Step 9 : Change the Format for both Sum of Count and Sum of Population to comma.
- Step 10 : Rename the Tooltips assigned previously to Market Share, Humana Members, and County Population respectively.
- Step 11 : Format the Filled Map visualization so that each county is colored according to the Sum of Market Share

        If value >= 0% and < 15% then "#D64550" (light red)
        If value >= 15% and < 25% then "#f0e199" (light yellow)
        If value >= 25% and < 100% then "#00FB22" (light green)
  
Formatting the map by market share makes it easy to distinguish different counties, and to clearly idenfity geographical trends in market share percentage.

- Step 12 : Retitle the map to Market Share by County, and then apply the Shadow effect to make the visualiztion jump out.

Snap of the newly created map visualization

![Map](https://github.com/user-attachments/assets/bf336f45-02ce-4520-9237-caa3e272a7b9)


Now build three separate Key Performance Indicators, used to measure how well Humana is doing in the state of Florida.

- Step 13 : Create a new Card visualization and drag Sum of Count to display the total number of Humana members in all of Florida.
- Step 14 : Change the Display units value to None within the Callout value setting, so that it's an exact number.
- Step 15 : Retitle the card to Total Humana Members and apply the Shadow effect.

        
Snap of the newly created KPI

![Total_Humana_Members](https://github.com/user-attachments/assets/a5947d7a-fb93-47e2-8db4-a52ea9159aa4)

        
- Step 16 : Create a new Card visualization and drag MMA Total to display the total number of Medicaid members.
- Step 17 : Change the Display units value to None within the Callout value setting, so that it's an exact number.
- Step 18 : Retitle the card to Total Medicaid Members and apply the Shadow effect.
- Step 19 : Change the format to comma.
        
Snap of the newly created KPI.

![Total_Medicaid_Members](https://github.com/user-attachments/assets/68a611b1-d186-4098-abb0-2c2f00aef4a7)

- Step 20 : Create a new Card visualization to display Humana's overall market share.
- Step 21 : Create a New measure to calculate the market share.

        Overall Market Share = SUM(data[Count])/SUM(data[MMA Total])    

- Step 22 : Drag the New measure to the card visualiztion.
- Step 23 : Change the Format to percentage and apply the Shadow effect.

Snap of the newly created KPI.
 
![Overall_Market_Share](https://github.com/user-attachments/assets/e5e49e5f-cc29-4504-8160-9d94736f80bc)

 
 - Step 24 : Create new Slicer visualization to add filtering capability for each county name.
 - Step 25 : Drag County Name to the newly created Slicer and change format to Dropdown.
 - Step 26: Turn the Selection for Show "Select all" to be able to select all counties at once, then add the Shadow effect.
 
Snap of the newly created Slicer
 
![Slicer](https://github.com/user-attachments/assets/8843dfd8-9e3f-444d-a85e-fa3b9647d9c3)

- Step 27 : Create the title banner by inserting the rounded rectangle shape.
- Step 28 : Match the color of the shape to the company branding color #00FB22.
- Step 29 : Add the title as October 2024 Florida Medicaid Report, resize text and rectangle banner as needed.
- Step 30 : Add bold text styling and black border to title banner.
- Step 31 : Insert company logo.
- Step 32 : Update background color of dashboard to light grey.

![Humana-Logo](https://github.com/user-attachments/assets/5dc69bc7-218a-4e05-aca0-ad496b8a4328)

- Step 33 : Create a New measure called Slicer Measure to be applied to the Slicer.

This new measure applies certain coloring depending on the percentage of market share in each county, just as previously. The IF statements are conditionals that apply certain colors if the county meets the right market share.

        Slicer Measure = 
        IF(
                data[Overall Market Share] > 0.25, "#00FB22",
                IF(
                        data[Overall Market Share] <= 0.25 && data[Overall Market Share] > 0.15, "#f0e199",
                        "#D64550"
                )
        )


 - Step 34 : Alter the map visualization color Format style to Field value, and then base it on the Slicer Measure just created.

 - Step 35 : The report was then published to Power BI Service.
 
 
![Published](https://github.com/user-attachments/assets/3f794432-8d1d-46d4-b7ea-6b52a14b4ad2)

# Snapshot of Dashboard (Power BI Service)

![Dashboard](https://github.com/user-attachments/assets/27956f64-e0e2-42f3-9f58-af295a6be3b6)

 
 # Report Snapshot (Power BI DESKTOP)

 
![Dashboard_Desktop](https://github.com/user-attachments/assets/7b824ac3-6223-4b1a-809f-56422530c879)

# Insights

* Counties shaded in light red (<15% market share), indicate areas where Humana's presence is limited compared to competitors. These regions are prime targets for marketing campaigns or partnership opportunities to increase Humana's membership.
* Counties with a high market share (>25%), marked in green, represent strongholds for Humana. These areas could benefit from resource optimization, reducing slightly without impacting membership so that other counties could gain growth potential.
* By examining the market share trends across Northern vs Southern Florida, Humana can tailor its growth strategies to align with the regions.
* This dashboard can help monitor how changes in Medicaid eligibility or benefits impact market share across counties, allowing for strategic adjustments in Humana's approach to its' members.
