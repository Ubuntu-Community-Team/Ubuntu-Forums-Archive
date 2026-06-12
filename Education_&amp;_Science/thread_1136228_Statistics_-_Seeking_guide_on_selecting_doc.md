---
title: "Statistics - Seeking guide on selecting doc"
date: 2009-04-24
forum: Education &amp; Science
---

### Post by satimis on 2009-04-24
Hi folks,


Statistics and PSPP (statistical computing) are completely new to me.  As curiosity I have PSPP installed on Debian 5.0.  It is now running.

# pspp myfile.syn

generating the file pspp.list.  I can read its content.


To satisfy my curiosity I started googling around documents on ;

statistical computing
statistics
t-test/anova/linear/regression/non parametric tests/etc.
etc.

in order to learn and found tons of documents.  I don't know where to start.


Could any folk shed me some light?  TIA


B.R.
satimis

---

### Post by euler_fan on 2009-04-25
Any decent undergraduate statistics textbook is the best place to start. Preferably if it does Bayesian statistics. Introduction to Bayesian Statistics would be a good one and gives you a chance to start learning R too.

As a note, if you decide you don't like Bayesian methods, it's pretty easy to drop the prior terms and become a frequentist.

---

### Post by satimis on 2009-04-26
> **euler_fan said:**
> Any decent undergraduate statistics textbook is the best place to start. Preferably if it does Bayesian statistics. Introduction to Bayesian Statistics would be a good one and gives you a chance to start learning R too.

As a note, if you decide you don't like Bayesian methods, it's pretty easy to drop the prior terms and become a frequentist.

Hi euler_fan,


Thanks for your advice.


I found follows concerning Bayesian statistics;


Bayesian statistics
[http://www.answers.com/topic/bayesian-statistics](http://www.answers.com/topic/bayesian-statistics)
[http://wapedia.mobi/en/Category:Bayesian_statistics](http://wapedia.mobi/en/Category:Bayesian_statistics)


A Brief Introduction to Bayesian Statistics
[http://www.pedrotytgat.be/wiskunde/statistiek/bayesian_approach_to_stats.pdf](http://www.pedrotytgat.be/wiskunde/statistiek/bayesian_approach_to_stats.pdf)

An Introduction to Bayesian Statistics
[http://www.scribd.com/doc/188520/An-Introduction-to-Bayesian-Statistics](http://www.scribd.com/doc/188520/An-Introduction-to-Bayesian-Statistics)
[http://ccrma.stanford.edu/~jos/bayes/](http://ccrma.stanford.edu/~jos/bayes/)
[http://bidug.pnl.gov/presentations/PEP/](http://bidug.pnl.gov/presentations/PEP/)
[http://www3.interscience.wiley.com/cgi-bin/bookhome/109855377?CRETRY=1&SRETRY=0](http://www3.interscience.wiley.com/cgi-bin/bookhome/109855377?CRETRY=1&SRETRY=0)


In fact google brought me tons of search results.  I wonder which of them will be the right road for me to go?


B.R.
satimis

---

### Post by sdbrogan on 2009-04-27
I think euler_fan may have been referring to 'Introduction to Bayesian Statistics' by William Bolstad. This is certainly very good - the only book I know of that presents a comprehensive view of statistics at an introductory level from a Bayesian viewpoint.  The only downside is that as well as R it uses Minitab (a non-free program) for its examples.

R is the free version of S, & I'd say if you could learn only one statistics app. it should be this one.  The command line interface might be daunting at first but GUIs like R Commander can help you over that first hurdle & it'll be worth it for the power & flexibility it gives you.  An introduction is here :

[http://cran.r-project.org/doc/contrib/Verzani-SimpleR.pdf](http://cran.r-project.org/doc/contrib/Verzani-SimpleR.pdf)

- & there's lots more stuff on the CRAN site.

The best reading for you depends on your level & where you want to go;  'Introductory Statistics with R' by Peter Dalgaard might be a good start.  More specialized books I can recommend include :

Linear Models with R - Faraway
Bayesian Computation with R - Albert
Time Series Analysis with Applications in R - Cryer & Chan

(Albert also has examples using WinBUGS, a program for simulating Markov chains, which will run in Ubuntu using Wine)

---

