---
title: "X-server disabled :("
date: 2006-06-29
forum: Desktop Environments
---

### Post by benny@linux on 2006-06-29
ive tryed to install compiz and the restart my computer ,when its up again its showing an error msg (ive copy it manualy)
Faild to start x server ... 
GDM : Xserver not found : /usr/local/bin/Xgl :0:0 -fullscreen -ac -acced xv -accel glx : pbuffer -auth /var/lib/gdm/: o.xauth -nolisten tcp vt+

error: command could not be executed!

please install the x server or correct GDM configurations and restart gdm

what to do???

---

### Post by NESFreak on 2006-06-29
try "sudo dpkg-reconfigure xserver-xorg"

---

### Post by benny@linux on 2006-07-03
thanks , its worked ..

---

