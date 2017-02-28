# Summary
This visualization shows the PM2.5 values of the two major cities in China, Beijing and Shanghai, from year 2012 to 2016. The air quality in China, especially for cities along eastern coast, is much worse than both the China and the US standards. Beijing has more serious air quality problem than Shanghai, and both cities have worse air quality in winter season. 
# Design
**Exploratory data analysis**
I downloaded the data from [U.S. Department of State](http://www.stateair.net/web/historical/1/1.html) which contains PM2.5 data of cities in China. In the beginning, I would like to compare air quality of all the five cities listed in the website. However, I noticed that only Beijing and Shanghai have completed data from year 2012 to 2016. A large amount of missing values exist in other cities' dataset. Therefore, the final visualization is about the two major cities, Beijing and Shanghai. 

Python is used to transform the data into yearly avarage to show the yearly trends. Also, I compute the daily average and categorize the average PM2.5 values into six categories defined [here](http://www.stateair.net/web/post/1/1.html). Monthly air quality levels percentage is computed based on the categories values for the two cities and showed in our side chart.
**Present the data**
The original data I obtained is a collection of hourly PM2.5 values of the two cities, based on which I would like to show the higher level trends of air quality changes. As mentioned above, I computed the daily average and then categorize the data into six levels.

First, I considered using bar chart as the example [here](https://bl.ocks.org/mbostock/3886394) in D3 to show the monthly air quality levels percentage. However, I noticed that it is not easy to add interactions like a hover, tooltip or interaction. Then, I found that dimple js is enough in this project and decided to build the visualization using dimple js. I found the similar bar chart example in dimple js [here](http://dimplejs.org/examples_viewer.html?id=bars_vertical_grouped_stacked_100pct). I also noticed that area chart might be a good choice in my case since it can give readers a holistic view of the air quality levels percentage.

Second, in order to show the yearly trends, I considered putting all years and months in the x axis and show all the data in one plot. Then I noticed that with either bar chart or area chart, we can tell that winter seasons have more serious air quality problem, but it is not very clear to show the overall yearly trends. Then I did some search and found that line chart with yearly average PM2.5 values is a better way to present the overall trends. There are also yearly average particulates standards created by different countries' government (https://en.wikipedia.org/wiki/Particulates). With line chart, I can visualize the higher level trends more clearly.

Third, to provide additional detailed montly trends of specific years, I used area chart as a side chart to show the information. However, dimple storyboard cannot work well with area chart. The explanation can be found [here](https://discussions.udacity.com/t/help-with-dimple-area-plot-animation/221859/4) (Thanks for the help in the forum!). I then changed back to bar chart since it is a still a good substitute in our case.

Fourth, to make the two plots more clearly, I changed the colors of the side chart and re-ordered the legend based on the feedback I got. I also added some comments and references to help readers understand the visualization better.
**Interaction and animation**
I added hover events to the line chart so that readers can view monthly air quality levels percentage in the side chart of the highlighted city accordingly. The selected line will be highlighted which is easier to view.

Tooltip is added to both charts automatically in dimple js.

Storyboard is used to show data of different years in the side chart.

**Note: Different versions can be found in Github repository**
# Feedback
**Feedback #1**
> If you order the months on the side chart, it shows a pattern more clearly that winter months have higher rates of "unhealthy" air pollution. The annotaion, and especially, the colors chosen make the charts very clear. It would be helpful if you add some commentary to the page (a few lines summarize the visualization).

*Change: Add orderRule to x axis. Add description text to the visualization.*

**Feedback #2**
> I noticed that the order of the legion in the stacked bar plot is just the opposite of the order of the plot itself. I understand that it might be the default setting of dimple, but if the order of the legend and the plot can be consistent, it would help people understand the plot more quickly.

*Change: Reorder the legend colors to make it consistent with the colors order in side chart.*

**Feedback #3**
> Although I am a big fan of animation, and I do think the changing chart looks really cool, it seems in this case animation is not helping the reader to reach a conclusion. I am trying to compare the year over year changes regarding monthly air quality percentage, however, I can only see one year at a time and it's hard to remember all the yearly patterns, so it's a bit hard to compare...Alternatively, maybe you could consider using an area chart1 with x-axis representing all the years and months. This way, the reader can have a holistic view instantly.

*Change: I choose not to put everything with area chart because: First, I didn't see clear yearly trends with one big chart, instead, line chart is better to provide the overall trends information. Second, the side chart is used to provide monthly trends within a specific year, for each year, winter season has more serious air quality problem. Third, area chart cannot work with storyboard in dimple js, therefore, bar chart is used instead.*
# Rescources
https://bl.ocks.org/mbostock/3886394
https://en.wikipedia.org/wiki/Particulates
https://discussions.udacity.com/t/help-with-dimple-area-plot-animation/221859/4
https://www.aqistudy.cn/historydata/monthdata.php?city=%E5%8C%97%E4%BA%AC
http://www.stateair.net/web/historical/1/5.html


