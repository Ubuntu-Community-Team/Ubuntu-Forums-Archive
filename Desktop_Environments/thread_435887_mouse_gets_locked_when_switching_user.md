---
title: "mouse gets locked when switching user"
date: 2007-05-07
forum: Desktop Environments
---

### Post by masterperas on 2007-05-07
I have recently installed edgy and then updated to feisty. 

at the moment whenever i try to switch user (without loggin out the first user) my mouse gets stuck and i can only regain control of it by switching back to the first user.

i am using gnome, and the login screen is the default one

---

### Post by snoop on 2007-05-08
I have the same problem. Running feisty on a dell inspiron 1150.

---

### Post by uzi09 on 2007-07-27
same as above thread

apparently this was a bug in edgy with ubuntu-screensaver, but you'd think they would have fixed it by now

---

### Post by dougalf on 2007-07-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/68370](https://bugs.launchpad.net/bugs/68370) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have this problem and for me it is due to a bug in the drivers for the touchpad. Unfortunately I have not had any success rebuilding the drivers as per the bug report

Another work around besides locking the screen before switching (which didn't always work for me) is to simply not use the buggy driver.

If you do not wish to comment out the Synaptics entry in their /etc/X11/xorg.conf and restart X you can simply move it aside:
```
cd /usr/lib/xorg/modules/input 
sudo mv synaptics_drv.so synaptics_drv.so.broken
```
and reboot.

It's not elegant but neither is the bug!

Unfortunately the synaptics driver adds a number of nice usability features to the touchpad so you may find that it now clicks where you don't want it to and the "move the scroll bar" feature on the side of the touchpad no longer works.

---

