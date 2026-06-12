---
title: "How to restore window manager to full function?"
date: 2008-01-05
forum: Desktop Environments
---

### Post by eworthy on 2008-01-05
I somehow borked the window manager when an update download failed.  The desktop looks normal but all windows open in the upper left corner of the screen and cannot be manipulated at all.  Cannot move, size or even close them via the mouse (can with Alt-F4).  The pager also does not work.  You can move windows to other desktops but you cannot switch to another desktop.

I would like to restore my system to the default starting point.   In fedora you could remove certain files in your /home directory and everything would get rebuilt on the next login.  How might I get a fully functional window manager working without doing a complete reinstall????

---

### Post by Sef on 2008-01-05
Have you tried this:

Alt+F2 > gnome-terminal > ```
sudo apt-get update
``` > ```
sudo apt-get install ubuntu-desktop
```

---

