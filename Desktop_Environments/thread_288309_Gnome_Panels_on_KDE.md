---
title: "Gnome Panels on KDE ???"
date: 2006-10-29
forum: Desktop Environments
---

### Post by DoorGunner on 2006-10-29
Hi

I recently updated to Edgy using upgrade distr method

Everything worked fairly well. However, I do have one problem.

when I start KDE I get gnome panels overlaping the KDE Panel. Gnome works fin e on its own....JUST KDE

Does anyone have a solution for this??

---

### Post by SendDerek on 2006-10-29
I once ran into a problem where the gnome icons and nautilus were sharing my KDE desktop.  A guy over at linux-noob.org helped me fix it by having me type this into the terminal:

```

killall nautilus

```

It worked for me, maybe it will work for you.  Unfortunatly, I don't have any other suggestions.  Good luck!

source: [http://www.linux-noob.com/forums/index.php?showtopic=2471&hl=](http://www.linux-noob.com/forums/index.php?showtopic=2471&hl=)

---

### Post by DoorGunner on 2006-10-30
Unfortunately that didnt work..... I still have the panels.....

---

### Post by kerry_s on 2006-10-30
Try> killall gnome-panels

---

### Post by DoorGunner on 2006-10-30
CRAP.... still there

> $ killall gnome-panels
gnome-panels: no process killed
john@DoorGunner:~$ sudo killall gnome-panels
Password:
gnome-panels: no process killed

---

### Post by DoorGunner on 2006-10-31
AAHH HAAA :D 

xkill did the trick.....:D

---

### Post by Hairy_Palms on 2006-10-31
also u needed to killall gnome-panel not gnome-panels ;)
make it run at kdestartup or something. i dont know how if kde has a session manager or anything as i never use it but i presume it should.

---

