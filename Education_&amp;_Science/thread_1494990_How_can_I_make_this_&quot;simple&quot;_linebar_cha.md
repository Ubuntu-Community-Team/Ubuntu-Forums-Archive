---
title: "How can I make this &quot;simple&quot; line/bar chart? (OpenOffice can't do it)"
date: 2010-05-27
forum: Education &amp; Science
---

### Post by lightbricko on 2010-05-27
Hi,

Is there some application I can use to make at least most of the quite simple line/bar chart I need? I have tried OpenOffice.Org Spreadsheet, but it seems to lack several of my needs.

I have attached an example of what I need (made partly in OpenOffice and then drawn by hand in Gimp). The example is based on the following data:
```
Time       AValue   AValueIsValidated   BValueMin   BValueMax
10:00:00   2        True                100         150
10:01:00   3        True                130         230
10:02:00   4        False               160         310
11:00:00   5        True                190         390
```

What I need is the following:

1. The x axis shows the time, so the horizontal distance between the elements with time 10:01:00 and 10:02:00 should be much smaller than the horizontal distance between the elements with time 10:02:00 and 11:00:00.

2. Logarithmic Y axis.

3. Bars that do not start from y=0, but instead has a min value and a max value.

4. Some indication that a specific value is not certain (or "validated"). In the example chart, I simply made the line dashed when it is connected to an object that is not validated, but this could be done in another way such as using a different color for the icon.

5. Highlight a period of time.

6. The bars and the lines do **not** have to be in the same chart if that isn't possible.

Thanks in advance!

---

### Post by dv3500ea on 2010-05-27
For more advanced graphing, try:
[scidavis]("apt:scidavis")
[labplot]("apt:labplot")
[grace]("apt:grace")
[gnuplot(CLI)]("apt:gnuplot")

---

### Post by scrogster on 2010-05-28
R ([http://www.r-project.org]("http://www.r-project.org")) is great for these kind of things. The following R code will produce a plot similar to your example. With a bit of practice you can easily code whatever sort of graph you might want.

```
library(chron)
dates<-c("01/06/10", "01/06/10","01/06/10","01/06/10")
times<-c("10:00:00", "10:01:00", "10:02:00", "11:00:00")
dttm<-chron(dates, times)
value<-c(2, 3, 4, 5)
valid<-c(TRUE, TRUE, FALSE, TRUE)
min.val<-c(100, 130, 160, 190)
max.val<-c(150, 230, 310, 390)
tms<-hours(dttm) +minutes(dttm)/60

plot(x=tms, y=log10(max.val), pch="", axes=FALSE, ylim=log10(c(1, 1000)), ylab="Value", xlab="Time")
polygon(x=c(10.2, 10.45, 10.45, 10.2, 10.2), y=log10(c(1, 1, 1000, 1000, 1)), col="skyblue", border=NA)
axis(2, at=log10(c(1, 10, 100, 1000, 10000)), labels=c(1, 10, 100, 1000, 10000), las=1)
axis(1, at=c(10, 10.25, 10.5, 10.75, 11.00), labels=c("10:00", "10:15", "10:30", "10:45", "11:00"))
segments(x0=tms, x1=tms, y0=log10(min.val), y1=log10(max.val), col="red", lwd=2)
points(x=tms, y=log10(value), col="blue", lwd=2, type="b", pch=1 +15*(valid))
title(main="Example chart")
box()
```

---

### Post by lightbricko on 2010-05-28
Thank you both for answering.

scrogster:
It was very helpful for me that you wrote the R code that does exactly what I need! I haven't used R before so I could probably have spent days just to write that code. 

After your post I installed RKWard, installed the chron package, ran your R code and it worked perfectly. I have attached the chart in case someone else wants to view it.

Is RKWard the "best" GUI for me? (I just picked the first one I found). My data sets will contain some thousand rows, and some columns are calculated. Currently I use formulas in OpenOffice.Org Spreadsheet and will either re-do it all in R or simply copy-paste the data from OpenOffice.

---

### Post by hubie on 2010-05-28
> **scrogster said:**
> The following R code will produce a plot similar to your example.

Thank you for the code snippet.  I picked up a couple of things there.  One thing I would change would be to add ```
log="y"
``` to the plot statement and then you don't have to worry about making all those log10 calls on the y-values.

---

### Post by hubie on 2010-05-28
> **lightbricko said:**
> My data sets will contain some thousand rows, and some columns are calculated. Currently I use formulas in OpenOffice.Org Spreadsheet and will either re-do it all in R or simply copy-paste the data from OpenOffice.

Because R is designed to do data manipulation and analysis, it is usually very easy to get your data into R.  You can save your OpenOffice data in comma-separated-value format and just import it into R with
```
mydata <- read.csv("mydatafile.csv",head=T,sep=",")
```
The "head=T" is assuming you have column headers, otherwise set it to False.  For instance, if the sample data you posted were in a datafile "mydata.txt", you could read it into R with
```
mydata <- read.csv("mydata.txt",head=T,sep="")
```
Once you have the data read in, you can do things like convert the data types into what you need, such as making a call to as.logical to convert those validation values into a boolean type.

---

### Post by PGScooter on 2010-05-28
just wanted to say +1 for R and graphics. If you plan on doing this more often, it is worth the pain and frustration sometimes accompanied with learning R.

Also check out ggplot2 for a very intuitive way of making graphs.

---

