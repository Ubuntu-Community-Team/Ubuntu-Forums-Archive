---
title: "Looking for a programme that does histograms"
date: 2006-12-05
forum: Education &amp; Science
---

### Post by clemkonan on 2006-12-05
Can anyone recommend a programme that will allow me to generate histigrams with class intervals.

Thanks

---

### Post by adamkane on 2006-12-05
Class intervals?

---

### Post by MacD on 2006-12-06
Gnumeric will do histograms with user-defined(in a range of cells) or calculated bins.

Tools-> statistical analysis-> histogram

There is also a histogram chart type in the charting tool options, but I have not been able to figure that out.

---

### Post by adamkane on 2006-12-07
There are lots of apps that do histograms. The best graphing programs these days seem to be written in java.

VOMegaPlot:
[http://vo.iucaa.ernet.in/~voi/VOMegaPlot_1_0_user_guide.htm](http://vo.iucaa.ernet.in/~voi/VOMegaPlot_1_0_user_guide.htm)

---

### Post by Campitor on 2006-12-09
> **clemkonan said:**
> Can anyone recommend a programme that will allow me to generate histigrams with class intervals.

Thanks

For me. The best program for graphs is R.  You can create histograms very easy with the hist() command. If you data (all of it, not the table results) is in a coloumn in gnumeric you can copy that coloumn (header included) in gnumeric and then you can do this in R:

```

#comment. to import data into an object called myvar 

myvar <- scan("clipboard", head=TRUE)

#for the histogram you can do

hist(myvar)

#if you want to specify specific categories

hist(myvar, breaks=c(break1,break2, etc))

#break1, break2 are numbers where you want the histogram classess

```

if you have a table, you can use the command barplot(). For help on these functions type ?hist or ?barplot in R.

Hope this helps

Camp

---

### Post by harishg on 2007-01-19
octave can do histograms.Never used it though.

---

