---
title: "stat software help"
date: 2010-05-28
forum: Education &amp; Science
---

### Post by mdshaver on 2010-05-28
I need to perform a two-way repeated measures ANOVA on linux but i dont know the easiest software to use as my only experience is with SPSS. I want to stick with one of the free options so my thoughts are Gnumeric, RLPlot, R, or Gretl. I know Gnumeric and RLPlot have built-in functions but I dont know how to perform Mauchly's Test of Sphericity. I know Gretl can perform the two-way ANOVA via the Other Linear Models option so that it is run like a regression analysis but I am honestly pretty weak in this area. Any help would be appreciated.

---

### Post by bryncoles on 2010-05-30
R is a very, very powerful software, but it's also very complex. You can get help on the internet, but it's not easy as you can't really google for 'r'. 

Try the following though:

```
www.rseek.org -- a search engine for general help
http://www.personality-project.org/R/ -- a guide to usage
```

Also, if you're using R try installing one of the GUI's available for it. That'll make it more accessible for you in the short term at least. I recommend Rcmdr.

Finally, if you install R you can launch it by opening a terminal and typing 

```
R
```

It took me far too long to figure that out when I started using R. You can launch R Commander by first launching R, then typing 

```
library(Rcmdr)
```


*****edit*****

Oh yeah, have a look at [PSPP](http://www.gnu.org/software/pspp/tour.html) and its GUI, PSppire. They're attempts to reimplement SPSS in an open source manner. They're also fairly incomplete but might be able to do what you want.

---

### Post by ugm6hr on 2010-05-30
> **bryncoles said:**
> R is a very, very powerful software, but it's also very complex. You can get help on the internet, but it's not easy as you can't really google for 'r'. 

I have recently decided to learn how to use R after dabbling with gretl.  This was a problem for me too.

A couple more useful sites to get to grips with R:
[http://www.statmethods.net/index.html](http://www.statmethods.net/index.html)
[http://www.r-tutor.com/](http://www.r-tutor.com/)

The former advertises itself as a guide for SPSS users, so perhaps is the best fit for you. Maybe this page: [http://www.statmethods.net/stats/anova.html](http://www.statmethods.net/stats/anova.html) 

I'm using the latter site myself, because it starts from the absolute basics!

---

### Post by spinoza666 on 2010-05-30
> **ugm6hr said:**
> I have recently decided to learn how to use R after dabbling with gretl.  This was a problem for me too.

A couple more useful sites to get to grips with R:
[http://www.statmethods.net/index.html](http://www.statmethods.net/index.html)
[http://www.r-tutor.com/](http://www.r-tutor.com/)

The former advertises itself as a guide for SPSS users, so perhaps is the best fit for you. Maybe this page: [http://www.statmethods.net/stats/anova.html](http://www.statmethods.net/stats/anova.html) 

I'm using the latter site myself, because it starts from the absolute basics!

Hehe got the R-bug that fast have we? Welcome to the R-junkie club:)

And for the query:

Start with this:
[http://cran.r-project.org/doc/manuals/R-intro.html]("http://cran.r-project.org/doc/manuals/R-intro.html")


Then do some searches on R-seek as already commented. You can also issue ?anova, ?lm, ?summary and so on to get yourself started with your analysis.

---

