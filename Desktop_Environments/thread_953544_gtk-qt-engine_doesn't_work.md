---
title: "gtk-qt-engine doesn't work"
date: 2008-10-20
forum: Desktop Environments
---

### Post by takowl on 2008-10-20
Since upgrading to Intrepid, gtk-qt-engine does not appear to load and theme GTK apps. The configuration screen in system settings is there, and it is definitely changing ~/.gtkrc-2.0-kde4, but GTK programs are still themed with the fallback blocky theme (Raleigh). There is no error message raised in stdout (tested on pidgin). I have tried purging the package and removing all files relating to it in ~/.* but with no change.

Any ideas why this might occur, or how I might go about finding out?

Reported as bug 285400, but no-one has confirmed it, so maybe it's just me seeing this.
[https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/28540](https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/28540)

---

### Post by bukharin on 2008-11-03
I can confirm this, but the bug report that you linked seemed to be something different.

Edit: Nevermind, you'd missed a 0, i confirmed your report there.

---

### Post by jasex on 2008-11-06
I concur as well... not changing theme, firefox and pidgin are ugly.

---

### Post by blacx on 2008-11-29
Try installing the package libbonoboui2-0

---

