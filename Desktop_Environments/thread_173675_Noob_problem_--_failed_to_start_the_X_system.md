---
title: "Noob problem -- failed to start the X system"
date: 2006-05-10
forum: Desktop Environments
---

### Post by jeffcollier on 2006-05-10
Just installed Breezy Badger (2.6.12-9-386) on a Compaq SR1630NX (AMD 64), using an old Dell monitor, with dual boot (Win XP).  On boot, the load appears to be going well until the "Failure to start the X system (graphical interface) error appears.  The system does not crash, but allows me to log in without a graphical interface.

I'm not so talented to know my way around yet -- I'm just trying to get something running for the 13 year old to learn.  

Is this a common problem with a known solution?

---

### Post by towsonu2003 on 2006-05-10
try ```
sudo dpkg-reconfigure xserver-xorg
``` in that non-graphical login, and try the default values. than try starting X with ```
startx
``` if it doesn't help, do the first command again and choose "vesa" when it asks you for a video driver. than startx... should work. the password it will ask is your own password. 

than check out the text-log file /var/log/Xorg.0.log for errors that stopped your X...

PS. This is a fairly common problem when your video device has no good drivers, or when ubuntu fails to recognize it... post your video card specifications so someone might help locating the driver...

---

### Post by jeffcollier on 2006-05-11
Many thanks.  The VESA driver did it.  Everything appears to be working to specs, including the dual boot, just as indicated in the wiki.

---

### Post by jeffcollier on 2006-05-11
Oh, regarding the video card: According to the liturature, it is an integrated one, using ATI radeon 200 chipset.

---

### Post by towsonu2003 on 2006-05-11
[QUOTE=jeffcollier]Oh, regarding the video card: According to the liturature, it is an integrated one, using ATI radeon 200 chipset.[/QUOTE]
than you can try the sudo dpkg-reconfigure command above from a terminal and choose ati this time... once you restart X, you'll know if it worked.

---

