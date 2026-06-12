---
title: "Stop xwindow from starting"
date: 2005-04-19
forum: Desktop Environments
---

### Post by fire59 on 2005-04-19
Currently I have KDE running.  I would like it  to not start up kdm or gdm not exactly sure what kubuntu is using.  But i would preferred to type in startx if I need to get to xwindow.  How do I remove it from startup?

---

### Post by Alexander Kirillov on 2005-04-19
[QUOTE=fire59]Currently I have KDE running.  I would like it  to not start up kdm or gdm not exactly sure what kubuntu is using.  But i would preferred to type in startx if I need to get to xwindow.  How do I remove it from startup?[/QUOTE]
 Try removing symlink /etc/rc2.d/S13gdm (or kdm, not sure what Kubuntu is using)

---

### Post by alastair on 2005-04-19
To stop GDM :

/etc/init.d/gdm stop

To remove the init link :

update-rc.d -f gdm remove

---

### Post by fire59 on 2005-04-20
thanx that work.  It was running kdm.

---

