---
title: "installing R on an AMD64 machine"
date: 2007-06-11
forum: Education &amp; Science
---

### Post by Alunah on 2007-06-11
Hi!!

I've been trying to install R (the statistical software) in my PC.  I'm working with Ubuntu 7.04 for AMD64 processors; I have not problem with the main program but I couldn't install any of the additional packages.  It just doesn't work. I've read in the FAQ of R website, that the binaries sources are available for i386 and various Linux version, but only for Debian and AMD64. The additional packages are tested as well just for Debian... 

Do I need to change from Ubuntu to Debian to fix this problem? Are someone here who was installed additional packages of R in an AMD processor using Ubuntu?

Thanks in advance...
:confused:

---

### Post by meatpan on 2007-06-11
How are you trying to install the R packages?  Are you using 'R CMD INSTALL' from the command line?  If not, run '?INSTALL' from within R for an explanation, or check out:[http://www.stat.psu.edu/~dhunter/R/html/utils/html/INSTALL.html](http://www.stat.psu.edu/~dhunter/R/html/utils/html/INSTALL.html)   

Also, consider '?install.packages' from within R.  This is a great way to retrieve or sync installed packages with CRAN.

I'm sure this is possible.  Many of the labs I work with use AMD64 with an extensive suite of R libs.

---

