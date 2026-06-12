---
title: "No longer able to access properties of vertical panel"
date: 2009-06-29
forum: Desktop Environments
---

### Post by 81wtbvi02 on 2009-06-29
While experimenting with the appearance of my gnome desktop, I made one of the panels vertical, on the left side of my screen.  It is the panel with the clock on it.  Now, whenever I try to change the properties of that panel by right clicking on it, I just get the properties for whatever panel applet is closest to where I click.  There doesn't seem to be anywhere that I can click to get the properties for the whole panel.

Is there some other way to access the properties of this panel?

I am running Ubuntu 9.04, Gnome 2.26.1.  The "About" screen of the other horizontal panel says "The GNOME Panel 2.26.0".  Here is the output of uname -a:
```
Linux HOSTNAME 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux
```

---

### Post by gettinoriginal on 2009-06-30
F2 then type gconf-editor > apps > panel

---

