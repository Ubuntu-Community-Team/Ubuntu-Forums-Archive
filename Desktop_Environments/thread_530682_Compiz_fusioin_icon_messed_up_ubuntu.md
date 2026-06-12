---
title: "Compiz fusioin icon messed up ubuntu"
date: 2007-08-20
forum: Desktop Environments
---

### Post by shorty28898 on 2007-08-20
first of all i cant ever cant compiz fusion to work on my intel graphics card, (help would be nice) secdonly, whern ever i do click on the compiz fusion icon, it makes my ubuntu mess up, only way to amek it normal is to restart it.  All the windows go away, and the title bars go away, and the panels all go away.

---

### Post by Happy_Man on 2007-08-20
Have you installed the proper drivers so that Fusion can run? 


And also, the command to get back normal windows and stuff is ```
metacity --replace
``` If you ever do it by mistake, just press alt+f2 and enter that command.

---

### Post by shorty28898 on 2007-08-22
I am not sure, can you help me install them?

---

### Post by Happy_Man on 2007-08-22
Well, go to System  --> Administration --> Restricted Drivers Manager, and have it install the drivers you need. Then try running Fusion again.

---

### Post by shorty28898 on 2007-08-22
there were no restricted drivers

---

### Post by miggols99 on 2007-08-23
Aren't Intel's drivers open source? So you won't need restricted drivers. Can you post your xorg.conf located at /etc/X11/xorg.conf?

```

gksudo gedit /etc/X11/xorg.conf

```

---

