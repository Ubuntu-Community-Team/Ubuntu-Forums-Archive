---
title: "Programs don't launch from menus"
date: 2010-10-11
forum: Desktop Environments
---

### Post by chuck9 on 2010-10-11
Just recently programs launched from a menu (e.g. gedit) quit working (they worked before).  This occurs on desktops "gnome-session" (:1, :2) that are accessed over vnc, but menu program launches work with the console.  The terminal sessions work on all.  Programs started from terminal sessions work.  A change has been the environment variable GNOME_DESKTOP_SESSION is no longer a number but a message saying it is deprecated.  

Any suggestions on how to track down the cause?

---

### Post by bobcollard on 2010-10-12
When something has been deprecated it is either replaced or simply removed from the current system for whatever reason.  You may be able to work around it by creating your own Launcher.  I use them in my Panel, it makes for a cleaner desktop.

---

