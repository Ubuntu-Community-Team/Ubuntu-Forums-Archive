---
title: "Installing R package Matrix under Ubuntu 8.10"
date: 2008-11-17
forum: Education &amp; Science
---

### Post by umor on 2008-11-17
Hello, 
this is more a report  than a question as I managed to solve my problem after serveral frustrating hours (yes, I am new to linux, but I think that others might still profit from my experince, so I decided to post here).
I am running R ([www.r-project.org]("http://www.r-project.org/")) version 2.8.0 (2008-10-20) on a Lenovo T61 laptop under Ubuntu 8.10.
When I wanted to install the R Package "Matrix" by ```
install.packages("Matrix")
``` in R I got many lines from the source code compilation and finally an error  "/usr/bin/ld: cannot find -lf77blas" and the package was not installed.
In order to make my R capable of building the "Matrix" package, I had to install the Ubuntu ATLAS package (Automatically Tuned Linear Algebra Software). To do so, I followed System->Administration->Synaptic Package Manager. There, I searched for "libatlas". I installed all packages where the description mentioned "Automatically Tuned Linear Algebra Software". Maybe less would do it as well, but I was not in the mood to figure out which packages are the essential ones. After installing all these (in my case 11) packages, I could install the "Matrix" package in R.
 
One more thing to mention: While I was googleing the issue, I read on [www.keittlab.org/node/158]("http://www.keittlab.org/node/158") that one should check if the computer supports SSE2 by 

```
grep sse2 /proc/cpuinfo
```

If it returns some text, then your CPU supports SSE2.

---

### Post by Creat on 2008-11-19
I ran in a similar problem. If it can help someone else, I figured that the package that solves this problem is one of the following:
libatlas-3dnow-dev
libatlas-base-dev
libatlas-test
libatlas3gf-3dnow

  However, it doesn't mean that other ATLAS packages are not necessary...

---

### Post by zeus77 on 2008-11-23
unless you have a fairly ancient CPU (pre-Pentium 4) the only ATLAS package you should need is libatlas3gf-sse2.  the others are unnecessary, and may even result in slower speed if installed since it may default to using the baseline atlas library, not one tuned for your CPU (not sure, this is complete speculation).  note that this is for 32-bit ubuntu.

for 64-bit, you just need libatlas3gf-base.

as an aside, it seems like the version of atlas in intrepid (3.6) is fairly old, as the latest version is 3.8.  

zeus77

---

### Post by mzuther on 2008-11-28
Hi!

Thanks to this thread I just managed to install another R package ("flowViz" from [www.bioconductor.org](www.bioconductor.org)) which had the same problem.  On both of my computers (Ubuntu 8.10 Intrepid, 32 bit), the installation of the package

  **libatlas-base-dev**

was enough.

Thanks, and have a nice week-end!

Martin

---

### Post by lgbpinho on 2009-04-26
Man, this helped me a lot... I really need the lme4 package which depends on Matrix. I just hope that libatlas3gf-sse2 doesn't make my cpu slower. Im a newcomer in Linux. I just loved R running under Linux. NOw back to the regression mixed models =).

Thanks a lot.

---

### Post by umor on 2010-05-09
Hi, 
when I updated from Ubuntu 9.10 to 10.4 the update could not complete due to an error when it tried to update the package "libatlas3gf-4dnow".
I read that it only to optimize procedures under a particular AMD hardware. Without knowing more about it, and, given the posts above, I would not recommend to install "libatlas3gf-4dnow" if you just have a problem to install your R packages.

Uli

---

