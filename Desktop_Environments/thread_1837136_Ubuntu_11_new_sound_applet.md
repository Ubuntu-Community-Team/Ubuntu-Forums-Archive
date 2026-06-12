---
title: "Ubuntu 11 new sound applet"
date: 2011-09-01
forum: Desktop Environments
---

### Post by edgreenberg on 2011-09-01
I have a pretty "experienced" home directory. It's existed (with Gnome) under Fedora, Centos, Ubuntu 8,9,10 and now 11.04.  I keep carrying all the dot (hidden) files along with me, and I get almost the same environment each time I upgrade or move things around. 

When I moved to 11.04, and set Gnome as my default instead of Unity, I got my old volume control instead of the new integrated sound controller, that appears in my Notification Area. 

I can kill the volume control, and keep it from starting on login, but I can't figure out how to get the new applet to start and run at all. 

Can anybody tell me what's going on under the hood and how to fix? 

Thanks, 
EdG

---

### Post by kerry_s on 2011-09-01
Remove gnome-volume-control-applet from startup, make sure you have indicator-sound installed.

---

### Post by edgreenberg on 2011-09-01
Thanks, Kerry,  Your suggestions got me on a good start.

I had to also remove the Notification Area applet and add the Indicator Applet (there were a bunch of choices for indicator applets with varying collections of indicators.)   That brought up a good collection of indicators, including the sound indicator.  Pidgin only shows up as a submenu of the Envelope Icon (connectivity?) so I re-added notificiation area, which surfaces the Pidgin icon. 

Ed

---

