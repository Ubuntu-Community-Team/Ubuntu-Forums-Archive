---
title: "XGL Again!!!"
date: 2006-06-05
forum: Desktop Environments
---

### Post by ufa on 2006-06-05
Hello all,
I installed XGL + Compiz in my Dapper Gnome following the steps in the wiki. It worked on my laptop (intel 915), but in my desktop it doesnt (Nvidia GForce 4 MX440). Apparently, when i choose the XGL session on login, it does not load the XGL server...it loads the X server instead. 
The XGL does work on nested mode, but not in the session chooser. I think it isnt  killing the X server and starting the XGL server. Is there a way to kill the X server  and start XGL with the "startxgl.sh" script by hand? Just to see the errors...
Thx in advance
Ufa

---

### Post by mattkenn4545 on 2006-06-05
Is XGL started with gdm.conf-custom?

---

### Post by ufa on 2006-06-05
No,
I killed GDM, and tried to start XGL manually, but i got:
 sudo startxgl.sh


bla bla bla
Fatal Server error:
no GLX visuals available

---

