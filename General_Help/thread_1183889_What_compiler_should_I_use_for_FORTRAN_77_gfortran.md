---
title: "What compiler should I use for FORTRAN 77? gfortran?"
date: 2009-06-10
forum: General Help
---

### Post by newagelink on 2009-06-10
**Question: Should I use gfortran to compile FORTRAN 77 code? If not, what should I use?**

From the Add/Remove... repository I found no Programming packages for FORTRAN 77. From the Synaptic Package Manager I found "fort77" and "gfortran". Initially I used fort77, since it appeared to be specifically for FORTRAN 77, but realized it invokes f2c which converts the code to C or C++. This seems less than ideal, if not problematic.

I found gfortran, but it appears specifically to be a FORTRAN 95 compiler. Being new to FORTRAN, [I know nothing of compatibility issues]("http://en.wikipedia.org/wiki/Fortran#Obsolescence_.26_deletions"), and am learning FORTRAN 77 because that is what I have been told [Dr. Bhattacharya]("http://physics.ucf.edu/profile.php?query=Bhattacharya") prefers for his research; I am helping him with his research for ten weeks.

What should I use to compile FORTRAN 77 code? A graduate student recommends ifort, but it is not present in the Synaptic Package Manager. Why isn't it, and what does that mean for a package to not be listed? I have tried [a Google search for ifort]("http://www.google.com/#hl=en&q=ifort&aq=f&oq=&aqi=g%3Ap1g9&fp=KUXUGZnmYHg"), but don't know where to get it or how to properly install it.

Your help would be greatly appreciated! Thanks.

*16:00 EST Update*: #ubuntu-offtopic told me that [g77 is a FORTRAN 77 compiler]("http://www.gnu.org/software/fortran/fortran.html"), and [the package]("http://packages.ubuntu.com/dapper/g77") I want -- but it is not included in Ubuntu 9.04 (Jaunty)! I have installed f2c as it translates FORTRAN 77 to C/C++, since gcc, the GNU C compiler, comes installed by default with Jaunty.

So, I've returned to converting FORTRAN 77 to C. Is this acceptable coding practice, especially since I have no idea how the conversion works?

---

### Post by sdennie on 2009-06-10
F95 is a superset of F77 with only a few exceptions: [http://www.ifremer.fr/ditigo/molagnon/fortran90/engfaq.html#1.0](http://www.ifremer.fr/ditigo/molagnon/fortran90/engfaq.html#1.0) so, as long as you are writing standard fortran, you will be fine with the gfortran compiler.  gfortran also has a "-std=legacy" flag that will not warn you if you are using deprecated features from F77.

---

