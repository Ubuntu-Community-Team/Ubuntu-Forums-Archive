---
title: "ksudoku build error..."
date: 2005-10-15
forum: Gaming &amp; Leisure
---

### Post by tommy04 on 2005-10-15
When I tried building ksudoku, it gave this error:

> checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

Obviously, I have X installed... any ideas why it can't find it?

---

### Post by Harleen on 2005-10-16
You will also need the development packages for X. Installing the package x-window-system-dev should solve this proplem (and uncover the next...).

---

### Post by thomax on 2005-10-16
The package you need is xlib-dev ;)

---

### Post by tommy04 on 2005-10-16
Well, I stumbled through the package requirements and ended up with this cryptic error:

> in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

Well, not as much cryptic as using bad grammar. But still... *huh?*

---

### Post by No6 on 2005-10-17
Doesn't the debian package work from [http://kde-apps.org/content/show.php?content=28792](http://kde-apps.org/content/show.php?content=28792) ?

---

### Post by tommy04 on 2005-10-17
> tommy@ubuntu:~$ sudo dpkg -i ksudoku_0.3-2_i386.deb
Password:
Selecting previously deselected package ksudoku.
(Reading database ... 82490 files and directories currently installed.)
Unpacking ksudoku (from ksudoku_0.3-2_i386.deb) ...
dpkg: dependency problems prevent configuration of ksudoku:
 ksudoku depends on kdelibs4 (>= 4:3.4.1-1); however:
  Package kdelibs4 is not installed.
 ksudoku depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing ksudoku (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ksudoku

There's no package called "libqt3c102-mt", but I did install "libqt4-mt" and "kdelibs4c2"...

---

### Post by No6 on 2005-10-18
Bugger!!

OK back to my usual workaround...

Download the rpm from the link above and alien it. You will need to install kdelibs-bin (plus deps) and libstdc++5. After you have installed these dpkg -i your newly created deb and all is well.

---

