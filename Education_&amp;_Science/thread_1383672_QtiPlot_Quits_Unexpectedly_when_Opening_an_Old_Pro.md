---
title: "QtiPlot Quits Unexpectedly when Opening an Old Project"
date: 2010-01-17
forum: Education &amp; Science
---

### Post by imobomi on 2010-01-17
I've been using the graphing program QtiPlot quite regularly now, for the last couple years.  Lately, however, I've been having problems getting it to open old projects.

I recently upgraded to Ubuntu 9.10 (Karmic), and ever since then, I've had this issue.  The program works fine for all other tasks, but when I try to open a saved project, it starts loading the various windows, and then suddenly quits with no error message or anything.  When running 9.04(Jaunty) or 8.10(Intrepid), I would occasionally see this problem, but found I could work around it by first saving the current project.  That option no longer works.

The only record I have that anything has happened, is a short message in the syslog:

Jan 16 15:15:17 d198-54 kernel: [ 6687.445548] qtiplot[3144]: segfault at 8 ip 08767575 sp bfdaed50 error 4 in qtiplot[8048000+1288000]

I have no idea what this means, though.

Originally, I had been using the qtiplot version from the repositories.  I've also tried running the free binaries from the website, but they all give me the same issue.

Anyone know how to fix this?  Thanks for your help!

---

### Post by imobomi on 2010-01-20
So, after much searching, and some conversations with Scott Howard and Divius, I've found at least a temporary solution to my problem.  The cause of the problem is still somewhat of a mystery to me, but it seemed to be some conflict between Qtiplot and the current versions of the Karmic libraries it depends on.  Anyway, here's what I did to fix it:

Solution:
1) Add Lucid repositories to your Software Sources by adding the following line:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse

2) Installed the newer version of Qtiplot (ver 0.9.7.10) using Synaptic (could have done this with apt-get too, I suspect).  It automatically install the new Lucid libraries.

Run Qtiplot, and it will now open old projects without crashing.  Hope it helps!

---

### Post by cmamyc on 2010-01-21
Thanks a lot, imobomi!
Same problem here, now solved thanks to you

---

