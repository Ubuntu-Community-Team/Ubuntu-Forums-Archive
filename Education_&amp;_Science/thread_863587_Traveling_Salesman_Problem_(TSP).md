---
title: "Traveling Salesman Problem (TSP)"
date: 2008-07-18
forum: Education &amp; Science
---

### Post by MeMooMeM on 2008-07-18
Hi!

Does anyone have experience with TSP using Linux? I could only find a TSP solver in GSL, but it's very complicated to use and they admit it :) I just have a list of Cartesian points:

```
 x   y
1.1 4.2
2.6 2.2
7.3 1.8
... ...
```

and I am trying to find the minimum path that connects these. Very simple. It is not important which one I start from.

Thanks a lot in advance!!
-MeMo

---

### Post by meatpan on 2008-07-18
Is there a particular task that you want for the TSP, or is it just the proof-of-concept you mention above?  If you only need to solve the problem above, why not experiment with your own greedy algorithm?

---

### Post by fsando on 2008-07-21
You could look at R. I'm absolutely sure someone has done something in R you could draw on.

[TSP in R]("http://www.google.com/search?q=traveling+salesman&domains=r-project.org&sitesearch=r-project.org&btnG=Google+Search")

Go here [http://cran.at.r-project.org/](http://cran.at.r-project.org/)

Click on 'packages' and look for the TSP package ;)

If you don't know R there is a great tutorial which you really need to go through first. Btw R runs on all the major OSes

---

### Post by MeMooMeM on 2008-08-07
> **meatpan said:**
> Is there a particular task that you want for the TSP, or is it just the proof-of-concept you mention above?  If you only need to solve the problem above, why not experiment with your own greedy algorithm?

The number of nodes may exceed hundreds of thousands :( I definitely need a heuristic approach! Thank you :)

---

### Post by MeMooMeM on 2008-08-07
> **fsando said:**
> You could look at R. I'm absolutely sure someone has done something in R you could draw on.


I have been playing with R for some time now and I must say I am impressed. I will definitely check the TSP package. I hope R allows C binding tough... Thanks!

---

