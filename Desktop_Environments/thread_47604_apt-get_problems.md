---
title: "apt-get problems"
date: 2005-07-09
forum: Desktop Environments
---

### Post by Elephantman on 2005-07-09
Hi,


I'm using hoary since it's release date, and over time I find more and more packages that have dependecies problems.
When I try to install a package, it has a dependencie but the highest version in hoary repository is not high enough. So basically I just cant access the package I want. The other case is that a dependecie is just not available (for example I want to install libavcodec-dev (a version is stamped ubuntu) but liba52-dev is not available).

Any easy solution ?

---

### Post by petehall on 2005-07-09
There is no easy solution, really. If you want the convenience that apt-get offers, then you have to accept that you're at the package maintainer's mercy in terms of updates. You may be able to get a newer version of the package from a different repository, or you may be able to pester the maintainer to offer the newer version. If you do go for this option, be prepared to grovel like mad.

---

### Post by Ptero-4 on 2005-07-09
[QUOTE=petehall]There is no easy solution, really. If you want the convenience that apt-get offers, then you have to accept that you're at the package maintainer's mercy in terms of updates. You may be able to get a newer version of the package from a different repository, or you may be able to pester the maintainer to offer the newer version. If you do go for this option, be prepared to grovel like mad.[/QUOTE]
 You can always add the debian repos or the repos for any other debian based distros.

---

### Post by DJ_Max on 2005-07-09
Do NOT use Debian repositories, unless you want problems. Use the official backports. 
[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)
[https://wiki.ubuntu.com//UbuntuBackports](https://wiki.ubuntu.com//UbuntuBackports)

---

