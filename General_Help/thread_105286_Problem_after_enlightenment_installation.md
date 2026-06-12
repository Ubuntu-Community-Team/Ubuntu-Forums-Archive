---
title: "Problem after enlightenment installation"
date: 2005-12-18
forum: General Help
---

### Post by antman90 on 2005-12-18
Hi Everyone

Just to start off with, I'm a newbie so I hope i don't sound too stupid.

I've been using breezy with gnome for a few weeks but wanted to try enlightenment, I tried installing it with synaptic, all looked like it went ok so I rebooted. When it started, there was no login screen, it just went to the terminal kinda screen. From there I can start enlightenment with 'startx' but I would rather just go back to using gnome (and have my logon screen back).

Any ideas on the config file/s that I would have to modify to get it back? I have installed a second copy of ubuntu on a second disk so I have access to all the configs in there original condition, just don't know which ones I need to mod on the other drive.

Thanks,
Anthony.

---

### Post by anil_robo on 2005-12-18
Did you make a backup of any files prior to installing enlightenment?
If you did, that'd be a file at /etc/X11/xorg.conf . If you made a copy of that file, try to find it in the same directory. If that doesn't exist, Ubuntu makes a copy of that file by defualt in the same directory, the name is "xorg.conf.xxxx" where xxxx is a 12 digit timestamp. If you find that file, delete your original xorg.conf and rename xorg.conf.xxxx to xorg.conf.
Reboot.
You should see light! :)

---

### Post by antman90 on 2005-12-18
Thanks Robo

But it didn't work, is there a config file that controls the login part, or is the login part of X? Does anyone know the command to launch the logon screen?

Thanks,
Anthony.



QUOTE=anil_robo]Did you make a backup of any files prior to installing enlightenment?
If you did, that'd be a file at /etc/X11/xorg.conf . If you made a copy of that file, try to find it in the same directory. If that doesn't exist, Ubuntu makes a copy of that file by defualt in the same directory, the name is "xorg.conf.xxxx" where xxxx is a 12 digit timestamp. If you find that file, delete your original xorg.conf and rename xorg.conf.xxxx to xorg.conf.
Reboot.
You should see light! :)[/QUOTE]

---

