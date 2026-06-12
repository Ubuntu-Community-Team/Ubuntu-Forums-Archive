---
title: "Window Manager/X issues"
date: 2008-07-20
forum: Desktop Environments
---

### Post by MrDetermination on 2008-07-20
I'm using GDM w/OpenBox & LXDM right now.  I want to use FLWM.  If I choose emergency xterm during login and enter "flwm" it'll launch, but that terminal sticks open and its kind of a hassle.

If I choose flwm from the list of options, it tells me /etc/bin/flwm isn't found but flwm lives in /usr/bin/flwm, so that isn't a suprise :)

---

### Post by Tim Sharitt on 2008-07-21
Edit the xsession file to reflect the proper directory. I should be /usr/share/xsessions/flwm.desktop or some thing very similar.

---

### Post by MrDetermination on 2008-07-21
Thanks, I never would have found that.

---

