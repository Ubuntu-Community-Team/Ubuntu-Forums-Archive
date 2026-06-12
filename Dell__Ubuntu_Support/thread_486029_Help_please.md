---
title: "Help please"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by weverjames on 2007-06-27
can someone explain me how to adjust the resolution to 1680x1050 please?
I am completely new to Linux.  I just received a Dimension loaded Ubuntu today.

---

### Post by arvevans on 2007-06-27
In Ubuntu with Gnome desktop it is at:

[INDENT]System - Preferences - Screen Resolution[/INDENT]

_._

---

### Post by dhruva023 on 2007-06-27
what graphic card do you have?

---

### Post by weverjames on 2007-06-27
i have an nvidia card (7500) and the 1680 x 1050 resolution is not in the default.  Therefore I need to add it.
The driver from Nvidia was already installed

---

### Post by Paul S on 2007-06-27
I thought dell was shipping it with the "nv" open source driver.  I didn't try that on my nvidia, but followed the wiki.ubuntu.com entry to install the "nvidia" driver.  It works fine.  Look in your /etc/X11/xorg.conf file to see what driver "nv" or "nvidia" it is using in the graphic card section.  If it's "nv", follow the wiki entry to change it.

HTH,

---

