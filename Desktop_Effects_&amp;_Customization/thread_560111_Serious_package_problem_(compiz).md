---
title: "Serious package problem (compiz)"
date: 2007-09-25
forum: Desktop Effects &amp; Customization
---

### Post by radicaledward on 2007-09-25
Some error with compiz, I just can't figure out how to fix it. I had several other repositories which may have generated the break, but I'm not sure which ones... Any help is greatly appreciated!!

panzer@golem:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  compiz-core: Breaks: libcompizconfig0 (< 0.5.2+git20070912-0ubuntu2) but 0.5.2+git20070829-0ubuntu1~ppa1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Edit:
Would it be helpful to force an earlier version of compiz, compiz-core, etc.. if so, which one and which version?

---

### Post by radicaledward on 2007-09-26
Agh, nevermind. It just got a lot worse. I'll just reinstall.

---

