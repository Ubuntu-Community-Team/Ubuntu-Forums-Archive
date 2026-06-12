---
title: "flashplugin-nonfree upstream change problems"
date: 2006-09-16
forum: Desktop Environments
---

### Post by threethirty on 2006-09-16
ok I tried installing flash from Automatix (don't start I like automatix) and I also tried installing from the CLI and here is what it spits out
```
three@Raptor:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
three@Raptor:~$ sudo update-flashplugin
automatic installation failed due to network problems or upstream changes
three@Raptor:~$

```
The "real world" problem is that when I open a flash it skips to the end of the file.  I have three Ubuntu boxes with the exact same outcome.  

any ideas

---

### Post by spur on 2006-09-16
I had this problem and ended up downloading from the adobe site and following their instructions. That worked.

---

### Post by jtbl on 2006-09-16
There is a bug in the package in the Ubuntu repos. This bug was caused by Adobe releasing version 7.0.68 a few days ago. This bug did get fixed in the Flash Plugin option in Automatix 6.5-3.

---

