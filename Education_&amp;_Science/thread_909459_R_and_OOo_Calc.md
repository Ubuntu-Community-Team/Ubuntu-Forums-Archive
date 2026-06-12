---
title: "R and OOo Calc"
date: 2008-09-03
forum: Education &amp; Science
---

### Post by tommers on 2008-09-03
I installed the addon for Calc that allows Calc to serve as a sort of front-end for R.

[http://wiki.services.openoffice.org/wiki/R_and_Calc]("http://wiki.services.openoffice.org/wiki/R_and_Calc")

I am able to output from R scripts to Calc, but I can't seem to read the data from Calc into R functions.

Does anyone have experience with this problem?

Thanks!

---

### Post by gunksta on 2008-09-05
I've had the same problem. I've not dug very deeply into it, but I think it's a bug with the extensio. I'm not sure how much development is ongoing right now. This could be a terrific way to extend Calc's number crunching capacity, but it's going to need more time to develop.

---

### Post by tommers on 2008-09-05
Thanks for your reply.  Oddly enough, the histogram function has worked a couple times.  The site shows that there have been something like 17000 downloads (if I remember correctly)... so hopefully it is still in development.  

I really like R for modeling - but it isn't the best for exploratory analyses like crosstabs and simply playing with data.  I've tried various frontends (JGR and Rcommander) but haven't been satisfied.  I was hoping that R4calc would do the trick well enough that I could persuade the rest of my research group to abandon SPSS... maybe someday.

---

### Post by gunksta on 2008-09-07
Check out PSPP. The version in the repos is old. If you know how to compile things, the version available on the website is great (comes with a GUI and everything). It's not a finished project yet, but it does cross-tabs and such like a charm, and is compatible with SPSS syntax.

--andy

---

