# Google Charts on Rails #

This is a very small wrapper plugin for the wonderful Charts API from Google.

[Google Chart API](http://code.google.com/apis/chart/)

## Installation ##

ruby script/plugin install http://google-charts-on-rails.googlecode.com/svn/google_charts_on_rails/


Once installed, start using it directly in your project.

## Example ##

```
GoogleChart.pie(10,20,40,30).to_url
```

which creates something like this:

![http://chart.apis.google.com/chart?chs=200x200&cht=p&chd=t:10,20,30,40&.png](http://chart.apis.google.com/chart?chs=200x200&cht=p&chd=t:10,20,30,40&.png)

### With labels: ###
```
GoogleChart.pie(['1997',10],['1998',20],['1999',40],['2000',30]).to_url
```

![http://chart.apis.google.com/chart?chs=250x100&cht=p&chl=1997|1998|2000|1999&chd=t:10,20,55,15&.png](http://chart.apis.google.com/chart?chs=250x100&cht=p&chl=1997|1998|2000|1999&chd=t:10,20,55,15&.png)

### or as Hash ###
```
GoogleChart.pie_3d_350x150('year 1997'=>10,'year 1998'=>20,'year 1999'=>15,'year 2000'=>55).to_url
```
![http://chart.apis.google.com/chart?chs=350x150&cht=p3&chl=year+1997|year+1998|year+1999|year+2000&chd=t:10,20,15,55&.png](http://chart.apis.google.com/chart?chs=350x150&cht=p3&chl=year+1997|year+1998|year+1999|year+2000&chd=t:10,20,15,55&.png)

### Pretty much anything would work: ###
```
GoogleChart.line_xy 
GoogleChart.bar_horizontal_stacked
GoogleChart.bar_vertical_stacked
GoogleChart.bar_horizontal_grouped
GoogleChart.bar_vertical_grouped
GoogleChart.pie
GoogleChart.pie_3d 
GoogleChart.venn
GoogleChart.scatter_plot
```

### which you can marry with the size ###

```
GoogleChart.pie_100x200(10,20,40,30).to_url
```

even
```
GoogleChart.100x200_pie(10,20,40,30).to_url
```

or do as crazy as
```
GoogleChart.pie_with_size_blah_blah_600x400('year 1997'=>10,'year 1998'=>20,'year 1999'=>15,'year 2000'=>55).to_url
```

### Lets do it the old fashioned way: ###
plain initialize
```
sales_chart = GoogleChart.new 
sales_chart.type = :pie
sales_chart.height = 200
sales_chart.width = 150
```
or initialize with size and/or type
```
sales_chart = GoogleChart.pie_3d_200x150
```
set data
```
sales_chart.data = [10, 20, 15, 55]
```
change the default colour with the hex code
```
sales_chart.colors = '346090'
```
get the url for the smaller chart
```
small_sales_chart_url = sales_chart.to_url
```

![http://chart.apis.google.com/chart?chs=200x150&cht=p&chco=346090&chd=t:10,20,15,55&.png](http://chart.apis.google.com/chart?chs=200x150&cht=p&chco=346090&chd=t:10,20,15,55&.png)

reuse object to change size and set labels for a bigger chart
```
sales_chart.labels = ['year 1997','year 1998','year 1999','year 2000']
sales_chart.height = 600
sales_chart.width = 350
big_sales_chart_url = sales_chart.to_url
```

## Support ##

This software was developed by [blj#rubyonrails](http://blog.7thcross.com) with guidance from rsl#rubyonrails

If you find it unpleasant, please [submit an issue](http://code.google.com/p/google-charts-on-rails/issues/list).