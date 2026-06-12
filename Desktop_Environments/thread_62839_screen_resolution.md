---
title: "screen resolution"
date: 2005-09-06
forum: Desktop Environments
---

### Post by yusof on 2005-09-06
i have problem to adjust my screen resolution in Ubuntu, when i click at Systems-->Preferences-->Screen Resolution, i just found 640 x 480 resolution, its so big size screen.  I also try to adjust using command **sudo / gedit /etc/x11/xorg.conf ** but i still dont know which part must make changes. Could anybody can help me. (sorry my english not good)

---

### Post by Perfect Storm on 2005-09-06
HorizSync 
VertRefresh 

You need your monitor spec to fill it out correctly or you might blew up you monitor.

---

