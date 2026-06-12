---
title: "Help installing library geoR in R, or update R"
date: 2006-11-13
forum: Education &amp; Science
---

### Post by Campitor on 2006-11-13
Hello All:

  I need some help installing library geoR in Ubuntu Dapper.  In Dapper, R is version 2.2. when I do

```
install.packages("geoR", dependencies=T)
```

it downloads a bunch of packages, and installs them, but complains about not finding package "sp".  When I try to load the geoR library, it won't do it because it lacks dependency 'sp'.  So I do:

```
install.packages("sp", dependencies=T)
```

package not found.  If I download the 'sp' package from CRAN, it won't install because it wants R version 2.4.  So here are my questions:

1.  Does anybody know where I can get an old version of the package "sp" so I can install it manually?

OR

2.  Does anybody know how I can upgrade to R 2.4 using deb's? where are those deb's? and won't I break something regarding packages already installed?

thanks

Camp.

P.S. Does anybody know of a good tutorial on Kriging for R or geoR.  I'm redoing all my analysis for my PhD thesis on R (did them originally on Surfer).

---

### Post by akniss on 2006-11-13
Standard disclaimer applies, but adding the following to my sources.list then aptitude upgrading worked for me.  The site is just one of the CRAN mirrors that usually has the latest versions.


```
## CRAN mirrors as repos to get latest R version
deb http://rh-mirror.linux.iastate.edu/CRAN/bin/linux/ubuntu/ dapper/ 

```

```
akniss@Dell-Laptop:~$ R
R version 2.4.0 (2006-10-03)
Copyright (C) 2006 The R Foundation for Statistical Computing

```

---

### Post by akniss on 2006-11-14
> **Campitor said:**
> 
P.S. Does anybody know of a good tutorial on Kriging for R or geoR.  I'm redoing all my analysis for my PhD thesis on R (did them originally on Surfer).

I'm not sure about a tutorial, but I have relied heavily on the geoR package documentation.  As far as documentation for contributed packages go, the geoR docs are some of the best.  

For kriging, I use variog() and variofit() in the geoR package to fit sample variograms; xvalid() in the geoR package for cross-validation; and finally the interp() function in the akima package and filled.contour() function in the graphics package to generate maps.

However, I have not done much kriging since R version 1.8, so the process may have been somewhat simplified by now.

---

### Post by Campitor on 2006-11-17
> **akniss said:**
> Standard disclaimer applies, but adding the following to my sources.list then aptitude upgrading worked for me.  The site is just one of the CRAN mirrors that usually has the latest versions.


Hello:

  Adding the repos worked in terms of upgrading. Afterwards, I ran:
```
update.packages()
```

and all extra installed packages were upgraded.  Now, when I load the geoR library, it is incorporated, but as soon as I try running kriging: 
```
krige.conv(data...etc.)
```
I get an error message, and R goes into:

Press 1 to abort (core dump)
Press 2 to abort 
Press 3 to exit without saving
Press 4 for normal exit.

The previous error is something about a missing memory address. I think I will uninstall everything and re-install again.  I'll let you knwo.  Thanks for your comments.

CAmp

---

### Post by akniss on 2006-11-17
> **Campitor said:**
> 
Press 1 to abort (core dump)
Press 2 to abort 
Press 3 to exit without saving
Press 4 for normal exit.

eek... that sounds serious... let us know if a reinstall fixes things.

---

