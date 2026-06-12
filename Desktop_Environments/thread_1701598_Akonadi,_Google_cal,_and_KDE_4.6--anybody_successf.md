---
title: "Akonadi, Google cal, and KDE 4.6--anybody successful?"
date: 2011-03-06
forum: Desktop Environments
---

### Post by mma8x on 2011-03-06
Upgraded to KDE 4.6 (and then 4.6.1).  Since then, I haven't been able to sync kontact with google calendar.  There is a [bug report]("https://bugs.kde.org/show_bug.cgi?id=264861") filed, but I haven't seen a whole lot about people having problems with this.  Is anyone syncing successfully?  I did a fresh 10.10 install on a spare drive, and it was working--upgraded to 4.6, and it stopped, and then did a (painful) ppa-purge to regress, and had it working again.

---

### Post by surml on 2011-03-07
Same here! Anyone?

---

### Post by cmkoch on 2011-03-24
Same here. Think i have to give up on Kontact ... :(

---

### Post by mma8x on 2011-03-24
Evolution works fine FWIW, and is much improved since I last tried it a few years back...

---

### Post by Alejandro Nova on 2011-03-25
The Kubuntu package is broken with KDE 4.6.

I compiled libgcal and akonadi-googledata from source, installed them, and now my Google info is syncing like a champ.

---

### Post by mma8x on 2011-03-26
Thanks for the tip.  I did the same (what a PITA! I haven't compiled anything in forever!) and all appears to be working now.  I also had to delete my old gcal-resource and create a new one.

---

### Post by nisavid on 2011-03-28
here are some relevant bug reports:

[https://bugs.launchpad.net/ubuntu/+source/akonadi-googledata/+bug/727487](https://bugs.launchpad.net/ubuntu/+source/akonadi-googledata/+bug/727487)
[https://bugs.kde.org/show_bug.cgi?id=264861](https://bugs.kde.org/show_bug.cgi?id=264861)

the KDE bug has step-by-step instructions by yartsa [1] for a workaround that uses ``apt-get source`` and dpkg-buildpackage to build fixed packages.

[1] [https://bugs.kde.org/show_bug.cgi?id=264861#c27](https://bugs.kde.org/show_bug.cgi?id=264861#c27)

---

### Post by Docaltmed on 2011-07-27
built the fixed packages, still didn't work!

---

