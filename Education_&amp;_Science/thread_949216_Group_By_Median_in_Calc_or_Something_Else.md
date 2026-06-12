---
title: "Group By Median in Calc or Something Else"
date: 2008-10-15
forum: Education &amp; Science
---

### Post by gunksta on 2008-10-15
I'm hoping someone here can save me a lot of wasted time and effort. I have a spreadsheet with information organized in the following way.

County     Variable
A              1.2
A              1.5
A              2.3
A              3.4
B              1.2
B              4.5
B              0.9

etc.

County is always a string and Variable is always a number.

I need to find the median for each county. There are over 70 counties in my list and each county may have a few hundred rows. The number of rows per county is NOT consistent. Obviously, I could go through and do this by hand, but it would take forever.

If someone has a clever way to do this, I am all ears.

My first instinct - it would be easy. I figured I was one pivot table away from happiness, but unfortunately, this has not proven to be the case. Pivot Table (Data Navigator) can not do median . . . . and average isn't the number that I need.

Ideas?

I am willing to consider other programs here.

I'm installing gnumeric right now to see if it can help me.

---

### Post by NikoC on 2008-10-16
Well I mainly work with R and there an option would be first to save your data as a .csv file and then read it out in R via:

data1<-read.csv(file="filename.csv",header=T,sep=",")

Your data should be organized in two columns, one titled "County" the other one "Variable" (using the names you provided in the example)

To calculate the median for county A:
median(data1$Variable[County=="A"])

For county B:
median(data1$Variable[County=="B"]

etc, etc, etc.

Good luck!

---

