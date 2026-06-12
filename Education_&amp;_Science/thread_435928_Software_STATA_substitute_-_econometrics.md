---
title: "Software: STATA substitute - econometrics"
date: 2007-05-07
forum: Education &amp; Science
---

### Post by eldepeche on 2007-05-07
Is there any program for GNU/Linux specifically made for econometric analysis (linear regressions, built-in hypothesis tests, instrumental variables, fixed/random effects models, and the like)?

I'm aware that such packages exist for R, but my few previous attempts at learning R syntax and such have produced nothing but a big question mark over my head.

I'm aware there is a version of STATA for Linux, but it costs an absolute minimum of $380 (that's with the educational discount; can't think of any students who can throw that down), which I can't quite spare at the moment. 

Thanks.

---

### Post by euler_fan on 2007-05-08
I'm sorry to hear that R didn't work out for you. It took me a long time to get the hang of it and I'm still barely more than a talented novice.

Good luck with your search.

---

### Post by akniss on 2007-05-09
I give this answer anytime someone gives up on R... but if you really want a powerful statistics program, R is well worth the time to learn.  And it will certainly take time.  It is not a simple syntax to learn.  But there is really nothing that can't be accomplished with R.  The reason I switched was because it is really the best option if you want to do complex analysis AND generate publication quality plots.  Most of the time programs with pretty GUIs will do simple analysis, and produce good plots, but aren't very powerful or customizable.  Programs that are similar in power to R (like SAS) are terrible at graphing.  R gives you both, if you are willing to take the time to learn how to use it.

---

### Post by anoir on 2007-05-09
I am a new econ phd (from Fall 2007 at U.S.) and have experience in Stata/R/Matlab/SAS for econometrics and simulation.

If you don't have any access to Stata, then R is the only viable alternative you have. It is less user friendly, but far more powerful and equipped with real programming capability (and beautiful plots). There are some free options like gretl:

[http://gretl.sourceforge.net/](http://gretl.sourceforge.net/)

I think, however, it is not yet ready for real use in serious study (if wrong, let me know).

SAS is outrageously priced. Matlab (or Octave/Scilab) is great, but not for your need.

By the way, I remember that Stata is offered for a lot cheaper price, if your instructor registers his or her class for Stata Corp...

---

### Post by eldepeche on 2007-05-09
Gretl looks like it's pretty good for undergrads working on a first course (and actually has a lot of datasets from Greene's book, which I used last year), but it's missing some important stuff. The panel data regression methods are greyed out in the menu, and since that's what I'm working on, it's of no use to me. I would keep an eye on it for the future.

Thanks everyone for your responses. Looks like I'll be taking the summer to learn R.

---

### Post by euler_fan on 2007-05-09
In R, in case you hadn't seen this, there a number of packages available that do many kinds of econometrics already. Not sure what all's in them but the package list is HUGE and someone has probably already done most of the legwork for what you want to do.

---

### Post by Cellular on 2007-06-04
> **eldepeche said:**
> Gretl looks like it's pretty good for undergrads working on a first course (and actually has a lot of datasets from Greene's book, which I used last year), but it's missing some important stuff. The panel data regression methods are greyed out in the menu, and since that's what I'm working on, it's of no use to me. I would keep an eye on it for the future.

Thanks everyone for your responses. Looks like I'll be taking the summer to learn R.

The reason panel data methods are grey in Gretl is that you don't have a panel data set open, or that you haven't made Gretl understand that what you have is panel data. In the data menu, there's and entry called Dataset structure, where you can specify your data as cross-section, time series or panel. 

I really do think you should look again at Gretl, it's very good and evolving rapidly. And, if you run into something you can't do in Gretl, it has a menu entry to automatically open R and import your open dataset into it. It is also possible for users to write new functions for Gretl.

---

