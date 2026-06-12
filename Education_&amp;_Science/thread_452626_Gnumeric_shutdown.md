---
title: "Gnumeric shutdown"
date: 2007-05-23
forum: Education &amp; Science
---

### Post by NikoC on 2007-05-23
Has anyone had the following problem? When I try to do a t-test with gnumeric the program just shuts down without any warning thereby not saving any changes made to the document. I know spreadsheets are not meant for statistics (I was just quickly comparing the same statistics with different programs, i.e. SPSS, Graphpad and Instat for Windows and R, gnumeric and open office calc for Linux), yet when the function is implemented, it should not behave like that... any thoughts are solutions?

---

### Post by tweedledee on 2007-05-23
> **NikoC said:**
> Has anyone had the following problem? When I try to do a t-test with gnumeric the program just shuts down without any warning thereby not saving any changes made to the document. I know spreadsheets are not meant for statistics (I was just quickly comparing the same statistics with different programs, i.e. SPSS, Graphpad and Instat for Windows and R, gnumeric and open office calc for Linux), yet when the function is implemented, it should not behave like that... any thoughts are solutions?

Don't use Gnumeric? :p  Seriously, it appears that all the "two-mean" tests are broken, although the others appear to work (I'd tried a few before, but not t-tests).  That marks the second time today I've managed to get Gnumeric to crash entirely like that - it also seems to do so if you format cells with an invalid code, then attempt to do anything else to those cells (including fixing the format code).  I'd suggest you file a bug report, assuming one doesn't already exist.

I do have to say that in general I've found Gnumeric to be quite reliable, even for some basic statistical analysis.

---

### Post by NikoC on 2007-05-24
Couldn't find anything related in the gnumeric bug list, yet there were already a few on launchpad. And similarly to your experience I enjoy using gnumeric, it's quick and lightweight and some statistics do indeed work (e.g. correlation).

[https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/95293]("https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/95293")
[https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/95959]("https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/95959")

---

### Post by raja on 2007-05-24
I (and others) have already [reported this]("https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/95293") in launchpad. Hopefully it will be sorted out.

---

### Post by brharri1 on 2007-08-04
I'm gonna jump in here and say that it is a segmentation fault. That way when people search for "gnumeric segmentation fault" like I did, this thread will come up :)

---

