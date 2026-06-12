---
title: "What is the *right* way of auto-starting programs in X?"
date: 2010-02-03
forum: Desktop Environments
---

### Post by EdMcMan on 2010-02-03
Hi all,

I have a question for you:

What is the *right* way of auto-starting programs in X?

I use the ion window manager normally, but occasionally switch to other wms using gdm.  Is there any way of autostarting programs without hardcoding my window manager?

For instance, as I understand it, using xinitrc or xclients files requires hardcoding my window manager.

I'd like to use gdm to select my window manager, and have xautolock start regardless of which window manager I use. 

Any suggestions -- or pointers to how xinit/Xclient/gdm work together -- would be appreciated.

---

### Post by Brandon Williams on 2010-02-03
If all of the window managers you use support the freedesktop standards, then you can control autostart using .desktop files in your ~/.config/autostart/ directory. This is true for Gnome, KDE, and Xfce, among others. I don't know whether it's true of ion though.

If some of the window managers you run are not freedesktop compliant, then for the programs that you want to have started for all window managers, you should be able to add the code for starting those programs to your ~/.xsessionrc file. This file is expected to contain shell code that works with /bin/sh (not bash), and the file will be sourced by the Xsession script when it runs.

---

### Post by EdMcMan on 2010-02-04
Thanks Brandon.  .xsessionrc is the right place.

Unfortunately, at least in Karmic gdm does not set the proper variables to source .xsessionrc:

[https://launchpad.net/bugs/475090](https://launchpad.net/bugs/475090)

There are fixes discussed in the bug.

---

