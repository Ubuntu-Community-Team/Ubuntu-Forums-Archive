---
title: "Starting Applications on Separate X Screens"
date: 2008-12-14
forum: General Help
---

### Post by jdralphs on 2008-12-14
Hello,

I am wondering if anyone has found a way to start applications on a secondary X screen.  My setup is this -- I am running Ubuntu 8.10 and Gnome, Restricted Nvidia drivers with dual screens running separate X screens.  I would like my screenlets to display, by default on my second screen.  

I can get screenlets to appear on my second screen if I launch screenlets-manager from there manually and then set the screenlets to be on that screen, but that only lasts for one session even after locking a screenlets' position.  

Is there a command or setting I can use that anyone is familiar with in oder to accomplish this task?

Thanks.

---

### Post by jdralphs on 2008-12-14
In the Sessions window, adding a "--screen=1" at the end of the command to start the screenlet seemed to do the trick!

---

### Post by kylemallory on 2008-12-23
I'm guessing the --screen=1 option is specific to your screenlets?

I'm trying to do the same thing with conky, but I can't seem to figure it out.  Any ideas?

---

