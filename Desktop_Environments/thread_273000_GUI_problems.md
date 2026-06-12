---
title: "GUI problems"
date: 2006-10-07
forum: Desktop Environments
---

### Post by civint on 2006-10-07
When I boot up my Ubuntu PC, usually it goes fine, it gets to the splash screen, I log on, fine. Until last night I downloaded some programs and libraries etc from synaptic, and when I started my PC up this morning it went straight to the command line, tty1 (up to tty6, as usual)I logged on, then I tried hitting <ctrl><alt><F7> to get to the GUI, logged on as myslef but no luck. So i did a quick google on another PC i own, thats hooked up to the web, and found out that If I gave the command "startx" it would start x windows, and the desktop environment. 
This was wonderful, but I fear only a temporary fix, I tried rebooting after getting an error message (in the GUI) about a setting daemon, so i rebooted, and it just took me to the command line again.

Can anyone help me? 

There are no error messages on startup that I can see, however I may simply have installed a bad package (as this is the only change i have made to my pc since the upgrades to my software)although I doubt this as I got all the packages from synaptic.

](*,)

---

### Post by SoggyCornflake on 2006-10-07
The first place I would check would be your inittab file.   It's found in the /etc folder.  This file tells your computer what to do when you startup (among other things)  There are different "run levels" and one of them is to come up to a command line interface, anohter is the GUI interface you want.

This is what part of mine looks like:

[B]# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.
[/B]
Confirm that the line that says default run level is set to what you want.

---

### Post by civint on 2006-10-07
I tried editing the bit that says
"id:2:initdefault:" to "id:5:initdefault:", but to no avail, so i changed back, otherwise mine is the same as it has been since i first installed ubuntu...

---

### Post by taurus on 2006-10-07
From a command line, try

```
sudo /etc/init.d/gdm start
```

---

### Post by civint on 2006-10-07
I tried what you suggested taurus, but after i hit return to execute the comman, nothing happened. However, in order to try it i logged out of the GUI, and I found an error message saying
"Error opening /dev/wavcom:No such file or directory
(EE) xf86OpenSerial:cannot open device /dev/wavcom
No such file or directory

SetGrabKeyState-disabled 
SetGrabKeyState-enabled"

does this mean anything to anyone?

---

### Post by taurus on 2006-10-07
What does your /etc/X11/xorg.conf look like then?  Or see if you can reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by civint on 2006-10-07
i tried to reconfigure the X using the command you gave, but alas, nothing, i just folowed through the motions, and that was that, it appeared to be the smae as before.

All I can think of is that something has skipped, or has been corrupted in  the startup, when I boot, because all that apperas to be wrong is that the GUI doesn't start up automatically, which is a right pain in the jacksie

---

### Post by taurus on 2006-10-07
If gdm doesn't start when you boot Ubuntu, try to remove it and install it again with

```

sudo aptitude update
sudo aptitude remove gdm
sudo aptitude install gdm
sudo /etc/init.d/gdm start

```

---

### Post by civint on 2006-10-07
okay, will let you know when ive done that.

---

### Post by civint on 2006-10-09
it worked a treat, thankyou for all your assistance, it has been much appreciated, I look forward to being able to help oithers with the same predicament.

---

