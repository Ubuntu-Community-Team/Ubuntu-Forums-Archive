---
title: "Display too tall for screen after clean install."
date: 2008-12-31
forum: General Help
---

### Post by DogWalker on 2008-12-31
I have just installed Ubuntu 8.10 on a new HDD added to my existing hardware. The copy is from Linux Format magazine and includes KDE and Xfce as well as Gnome. I have been using Kubuntu for about 2 years.

When running from the live CD I noticed that the Gnome interface didn't fit my screen properly (too tall - the panels at the top and bottom were only partly visible) but I thought this would be okay after installing.

It wasn't - the same problem occured, making it hard to use the panels.  I rebooted and switched into KDE and got the same problem. With the top of the screen in view the bottom panel is unusable.  But bringing the vertical alignment up so the bottom panel is clear takes away the top of the screen.

In KDE I tried resetting the screen resolution and System Setting froze leaving me no option but to turn the power off and reboot.  Switching into Xfce helps because there are no panels, but I really want to use KDE.  In Gnome I can change the resolution as expected but this has no effect on the problem.

My 19" flat screen has been properly detected at installation.

Can anyone help me please?  I did not have this problem in previous versions.

DW

---

### Post by dcstar on 2008-12-31
> **DogWalker said:**
> 
.........
It wasn't - the same problem occured, making it hard to use the panels.  I rebooted and switched into KDE and got the same problem. With the top of the screen in view the bottom panel is unusable.  But bringing the vertical alignment up so the bottom panel is clear takes away the top of the screen.
........
My 19" flat screen has been properly detected at installation.

Can anyone help me please?  I did not have this problem in previous versions.


Make sure any video hardware driver is installed and use the "Auto sync" function on your monitor.

---

### Post by DogWalker on 2009-01-01
Yes, I had tried that, and without success.  Eventually the problem was resolved (at least in Gnome) by resetting the resolution and adding a series of Display subsections to xorg.conf.  As far as KDE is concerned, it still freezes everything when I try to access the Display section of  System Settings and I can't be dealing with that, so I am a Gnome convert.  Anyway, I am not keen on KDE4.

DW

---

