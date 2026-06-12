---
title: "gnumeric solver use"
date: 2008-11-15
forum: Education &amp; Science
---

### Post by hollowhead on 2008-11-15
Can anyone tell me whether its possible to use gnumeric solver w/o having to enter constraints.  I've been trying to test whether the chemical assay I'm using is running parallel using a method described by Reeve (2000).  The easiest way to do this is to use a solver.  OOcalc solver does not do non-linear problems at the moment although it will converge if you are very close to a solution.  Gnumeric seems to require you to enter constraints when other solvers don't.  I had to use excel at university.  Any way round this?  Ta.

---

### Post by jbrefort on 2008-11-16
You ca add a simple constraint which will always be satisfied. If you have one vairable that you know will be psitive, it should be OK. Anyway gnumeric solver handles only linear problems as far as I know. 
I've heard of someone who proposed to implement a non linear solver, but it seems that this code never landed.

---

### Post by hollowhead on 2008-11-16
Cheers guess I'll have to use excel for now.

---

### Post by kaspar_silas on 2008-11-19
Sorry if I am missing something but are you saying excel has a non linear solver that doesn't need estimates? If this is the case it's almost certainly dangerous to use these results. 

In my understanding Non linear solvers find the nearest local minima. Some are a abit smarter than just "rolling down the hill" but many aren't. So whilst the results you obtain without estimates may be the correct answer it is not certain. Further more it is not certain that it is even close to the correct answer. 

In short if you are doing this as publication quality work I would be very careful about excel. 

Check out. 
[http://portal.acm.org/citation.cfm?id=1162012]("http://portal.acm.org/citation.cfm?id=1162012")
[http://www.practicalstats.com/xlsstats/excelstats.html]("http://www.practicalstats.com/xlsstats/excelstats.html")

---

