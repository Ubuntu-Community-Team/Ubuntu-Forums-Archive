---
title: "Creating a custom keymap"
date: 2008-11-30
forum: Desktop Environments
---

### Post by plaa on 2008-11-30
Hi,

For years now I have used a custom keymap, where I have changed the Caps lock key to be another return and a few other tweaks.  Yesterday I updated to Intrepid and have been trying to get the same, but without luck.

Previously I have created the custom layout by adding my own layout variant to /usr/share/X11/xkb/symbols/fi, and configuring /etc/X11/xorg.conf to use that variant.  Now, however, the xorg.conf does not include the keyboard configuration and adding it doesn't help.  I cannot find the custom layout variant in the settings manager's keyboard settings either (in Xubuntu).  I've also tried adding the variant to /usr/share/X11/xkb/symbols.dir but that doesn't help.

What has to be done to add a new keyboard variant to the system?  In what configuration file is the keyboard layout set?  Should it be performed already in HAL or some other place?  I guess I could add my whole previous X configuration (including the Screens and ServerLayout), but that doesn't seem the right way to go.

Thanks for any help!

---

### Post by mali2297 on 2008-11-30
I use **xmodmap** for such tasks. See the man page or search the web for tutorials. Here's one on remapping Caps Lock:
[http://praveen.kumar.net.in/journal/2008/06/14/modifying-control-and-caps-lock-keys-under-opensolaris-and-linux/](http://praveen.kumar.net.in/journal/2008/06/14/modifying-control-and-caps-lock-keys-under-opensolaris-and-linux/)

---

