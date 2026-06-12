---
title: "Disable XFCE Sessions"
date: 2007-02-05
forum: Desktop Environments
---

### Post by exoren22 on 2007-02-05
XFce has cool session saving ability that can be really cool. I have errors from the fact that I have a lot of the same programs starting up in gnome, and I have gnome compatibility on. Can I delete my session saving so that I don't get two instances of all of my programs popping up every time I log into XFce?
Thanks.

---

### Post by aysiu on 2007-02-06
There isn't an option to not save your session at logout?

---

### Post by kerry_s on 2007-02-06
menu> settings> sessions and startup

---

### Post by exoren22 on 2007-02-06
I did that, but I still get two nm-applet's starting up always when I start my session. I saved a session with nothing started from gnome, and I haven't saved a session since. I wanted to know if there was a file I could alter or at least look in to find out why I get two network managers competing for bandwidth for the same task.

---

### Post by SnackySmores on 2007-04-23
check the files in ~/.cache/sessions/   delete the xfce-session* files to solve the problem 
take care

---

