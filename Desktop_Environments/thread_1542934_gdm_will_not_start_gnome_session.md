---
title: "gdm will not start gnome session"
date: 2010-07-31
forum: Desktop Environments
---

### Post by sirjasonr on 2010-07-31
Hello :)

I'm having issues logging into my system... After authenticating via GDM, the screen goes black with only the mouse showing and remains this way indefinitely. At first the hard disk is active to a similar degree as it was when logins were successful, but then the system (apart from being able to move the mouse) is unresponsive.

If left for long enough so that the screen goes into power-saving mode, moving the mouse brings up the unlock dialogue that you normally get if you set your computer to lock itself after a period of idleness.

I suspect some sort of file corruption, as I have not changed any settings recently. I have forced checks on all of my disks in the hope it would solve this problem. I have also tested logging in on a freshly created user account I created which gives the same result. Also, starting an xterm session from GDM works fine.

If anyone knows how I can troubleshoot the GDM login process, such as by pointing out any useful log files and alike, I would be incredibly grateful!

Thanks for reading!

Cheers,
Jason

---

### Post by Zorgoth on 2010-07-31
Are you using any device drivers like the ATI or nVidia drivers from their website?  Such drivers have to reinstalled every time the kernel is updated.  If you got the (older) drivers from System>Administration>Hardware Drivers this should not happen, but if you are using proprietary graphics drivers this could happen each time your kernel is updated.  If this is the problem, then put the driver installer somewhere on your hard drive if it isn't already there (you can use a live CD to do that), and then boot into "recovery mode" and get a root shell.  You can then use that shell to install and set up whatever you need.

---

### Post by falcon1620 on 2010-07-31
I have the same problem with a Asus board with an integrated video chip set from Nvidia, one of the 8000 series I think. Its AM2 socket. Are you using an Integrated Nvidia Card and driver? I don't think that his issue is related to the proprietary driver more that a particular chip set not being supported with it on LTS, The older Ubuntu ran fine with it until the person who owns the computer decided to push the "upgrade" button. ;)
I gave up on mine, I am hoping that a newer Nvidia card will solve my problem.I need an Nvidia card for my projects. No kernel updates were involved in my case. I would file a bug, but I have been to lazy. What happens is that the GDM on mine loads up, then all of a sudden drops out of Gnome and issues no error, he is probably back in "Bash" just like I am. If you log in sirjasonr in the console using your user name and password you gave during the installer, you can type "startx" and it will load up gnome just fine. That's really a pain. I can not find out where or how to fix the gdm issue yet though, not a permissions issue, or any thing like that. Manually invoking GDM later on also helps. But no sense in manually starting the service, I have also checked and yes the service does come up on boot then drops out.

---

### Post by sirjasonr on 2010-07-31
Thanks for taking the time to reply!
I managed to get things live and kicking again by removing all nVidia packages
```
sudo apt-get --purge remove nvidia-*
```

and installing the latest proprietary driver (256.35).

Thanks again :)

Jason

---

### Post by falcon1620 on 2010-08-01
Nice! Glad you got it going... :p

---

