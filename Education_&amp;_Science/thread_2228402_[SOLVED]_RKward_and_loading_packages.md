---
title: "[SOLVED] RKward and loading packages"
date: 2014-06-07
forum: Education &amp; Science
---

### Post by Neil_Hollow on 2014-06-07
I have some stats to look at for someone I'm helping to mentor in Cambodia.  I installed PSPP and its pretty good now.  But the version I'm using does not have the KW test which I think we need.  I found RKWard and installed it and again it looks good.  However, again KW test is missing and its parametric equivalent 1 way ANOVA.  I think its in one of the packages, but I first I do not know which one and second I cannot get them to configure from within RKWard.  I tried running RKWard as root to do this as well  The package is added either way but next time you come back into RKWard its back in the installed packages not the loaded packages.

Ta.

---

### Post by rewyllys on 2014-06-07
I'd recommend that you install the R statistical package plus RStudio, which I find much more amenable than RKward.  R includes the Kruskal-Wallis test.

You can install R by beginning with using the Syntactic Package Manager to install r-base, and the SPM will also install RStudio as rstudio.

---

### Post by Neil_Hollow on 2014-06-07
rewyllys, thanks for your reply.  I tried your suggestion and I don't think its quite what I want.  Rstudio looks hard work for someone who has never used R before. RKWard is graphical and I can see how to run the tests its just I cannot work out how to get the test there in the first place.

---

### Post by rewyllys on 2014-06-07
> **Neil_Hollow said:**
> rewyllys, thanks for your reply.  I tried your suggestion and I don't think its quite what I want.  Rstudio looks hard work for someone who has never used R before. RKWard is graphical and I can see how to run the tests its just I cannot work out how to get the test there in the first place.
I think you'll find it useful to make sure that you've loaded R via the Synaptic Package Manager, as I suggested in my previous post.

Then I recommend that you add a repository for R to your SPM repositories.  Having such a repository in your config file makes it easy to tell RKWard to obtain this or that test procedure.

Here is a [thread that explains how to add an R repository]("http://ubuntuforums.org/showthread.php?t=2127394&highlight=repository").  You can find a list of repositories at the Mirrors option at [http://cran.r-project.org/](http://cran.r-project.org/).  I personally like to use the mirror at the University of California, Los Angeles (UCLA), but the general guide is to use a mirror reasonably close to your location.

Here is one tutorial (a brief one) on using the Kruskal-Wallis test in R.  There are other tutorials; just Google "tutorial Kruskal-Wallis test R statistical software".

Good luck!

---

### Post by Neil_Hollow on 2014-06-07
Thanks I've worked out how to do a anova in RKWard annoyingly its not possible to do by using the graphical methods like SPSS etc unlike a lot of other stuff (eg, t test, Wilcoxen).  Also found the KW test (both in stats4 package for anyone interested).

---

### Post by rewyllys on 2014-06-07
I'm glad to hear of your success.

---

