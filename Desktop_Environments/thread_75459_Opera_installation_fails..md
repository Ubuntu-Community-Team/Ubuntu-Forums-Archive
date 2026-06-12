---
title: "Opera installation fails."
date: 2005-10-13
forum: Desktop Environments
---

### Post by Adam Lee on 2005-10-13
```
opera_8.50-20050916.6-shared-qt_en_etch_i386.deb  Screenshot.png
adam@ubuntu:~/Desktop$ sudo dpkg -i opera_8.50-20050916.6-shared-qt_en_etch_i386.deb
Selecting previously deselected package opera.
(Reading database ... 60616 files and directories currently installed.)
Unpacking opera (from opera_8.50-20050916.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on xlib6g (>= 3.3.6) | xlibs; however:
  Package xlib6g is not installed.
  Package xlibs is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera
```

I searched for xlib6g on Synaptic, but nothing came out.
Any suggestions?

---

### Post by Ampersand on 2005-10-13
Try installing xlibs from Synaptic.

---

### Post by aysiu on 2005-10-13
I've found the Other/Static.deb from Opera's site works fine without needing dependencies (as opposed to the one that's specifically for Ubuntu).

---

### Post by Lambert on 2005-10-13
I've found that setting up the plug-ins is easier on the static version.

---

### Post by Adam Lee on 2005-10-14
It works now with the other/static package!
Thx a bunch!

---

### Post by Adam Lee on 2005-10-14
Hm... The font of the menu(File, Edit, View etc...) look ugly. 
Is it normal??

---

### Post by aysiu on 2005-10-14
[QUOTE=Adam Lee]Hm... The font of the menu(File, Edit, View etc...) look ugly. 
Is it normal??[/QUOTE] Define "ugly." Do you have a screenshot?

---

