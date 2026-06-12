---
title: "Which Fortran compiler for Compaq VS Source?"
date: 2009-04-29
forum: General Help
---

### Post by whaler1 on 2009-04-29
Hi, I have a bunch of source code originally written for Compaq Visual Studio 6.6b that builds DOS based executables.  I want to compile for use on ubuntu 8.10.  I have tried using gfortran 4.3.2-1ubuntu12 but I end up with a daunting list of errors.
 
Has anyone got any advice for how to best approach this task?  I am wondering if there is a more suitable fortran compliler that I should be using.

---

### Post by mb_webguy on 2009-04-29
g77 and gfortran are the two open-source Fortran compilers for Linux.  gfortran is the newer of the two, and supports Fortran 95.  Unfortunately, Visual Fortran apparently doesn't quite conform to standard Fortran, so it won't compile cleanly on either.

There *is* a Visual Fortran compiler for Linux -- the Intel Fortran compiler, but it's a commercial version.  You can get it free for non-commercial use [here]("http://software.intel.com/en-us/articles/non-commercial-software-development/"), but if you're going to use it commercially, the license is close to $900.

---

