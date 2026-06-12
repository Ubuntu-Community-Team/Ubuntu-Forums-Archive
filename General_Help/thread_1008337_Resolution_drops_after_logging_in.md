---
title: "Resolution drops after logging in"
date: 2008-12-11
forum: General Help
---

### Post by microcentillion on 2008-12-11
Hey All..

I have recently gotten my Dapper image in xVM VirtualBox running at the correct resolution, but there is an issue that I have run into.

My Native screen resolution is 1440x900, and the login screen uses exactly that - however, once I log in, the resolution drops to 1280x800. The desktop display properties don't show 1440x900 as being available, but I can use 'xRandr -s 0/1440x900' to achieve the desired resolution. I am working around this annoyance by having an Auto-started Application to run the xRandr command for me, but having the screen resizing twice at login not only looks tacky, it also causes problems for the mouse in VirtualBox.

Se here's the question: What can be done to stop xubuntu from changing the resolution at login?

---

### Post by MCrittenden on 2008-12-11
Please post the contents of /etc/X11/xorg.conf

---

