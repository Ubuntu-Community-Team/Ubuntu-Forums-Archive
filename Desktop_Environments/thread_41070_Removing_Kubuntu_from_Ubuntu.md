---
title: "Removing Kubuntu from Ubuntu"
date: 2005-06-11
forum: Desktop Environments
---

### Post by adamb10 on 2005-06-11
I installed Kubuntu alongside my Ubuntu install.  After evaluating it I want to remove it.  I try apt-get remove kubuntu-desktop but it says it's not installed.

---

### Post by Xian on 2005-06-11
Read [THIS](http://ubuntuforums.org/showthread.php?t=22652) thread for some helpful information.

---

### Post by az on 2005-06-11
sudo apt-get remove --purge kdelibs4 arts

Debfoster may be overkill.  Like using amonia to clean up spilled juice.

---

### Post by Xian on 2005-06-11
Some prefer to wring out the mop after removing the spill.  :grin:

---

