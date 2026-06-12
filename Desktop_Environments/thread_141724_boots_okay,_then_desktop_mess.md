---
title: "boots okay, then desktop mess"
date: 2006-03-08
forum: Desktop Environments
---

### Post by kaaawa on 2006-03-08
I installed ubuntu on a partition w/ a swap partition and can dual boot win XP.  I'm new to linux so I don't know the commands.  Anyways, the ubuntu splash screen shows everything loading ok except for the time (which I'm guessing needs a network connection).  When Gnome is supposed to load the desktop it is a mess of the word ubuntu and small lines of orange overlapping each other.  Mouse pointer works, but no menus to adjust anything.  The laptop is a Medion Titanium MD 2900 w/ NVIDIA Geforce 440 GO 64MB.  Screen has native resolution of 1280x854 pixels, but that is all i know about it.

---

### Post by RAOF on 2006-03-08
Ok, this is probably a graphics card issue - the default drivers ("nv") sometimes have with newer cards.  Try booting into "recovery mode", and running
```
dpkg-reconfigure -phigh xserver-xorg
```
The first thing it will show you is a list of graphics drivers - select the "vesa" drivers.  Finish the configuration stuff - unless you know better, the defaults are fine.

Now, type "exit", and Ubuntu should continue booting to the GUI.  And it should work ;)

For a better fix, check out the "nvidia drivers" link in my sig.

---

### Post by kaaawa on 2006-03-10
Worked great, thx!

---

