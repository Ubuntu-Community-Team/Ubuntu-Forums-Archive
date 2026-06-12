---
title: "xubuntu 18.04 lost menu."
date: 2018-07-26
forum: Desktop Environments
---

### Post by khPWXxF on 2018-07-26
I am trying to set up mythtv on a ASUS M3N78-EM mobo with AMD CPU and Nvidia 8300 onboard graphics.  This system is stable with Ubuntu 14.04.
I have installed XUBUNTU 18.04 and loaded what I hope will be stable nvidia driver 304.106.

My problem is that this afternoon the desktop lost its main menu icon.  The desktop has the pretty green/blue panel with icons for the mounted partitions and the recycle bin.  It has a black bar at the top.  The black bar has bluetooth, ethernet and time entries on the right and previously had a little icon at the far top left on the black bar which brought up the main menu  (settings, closedown, multimedia, browser etc).  That has now vanished.

There are two entries in /var/crash which were created about that time.

> linux-image-4.15.0-29-generic.121636.crash
linux-image-4.15.0-29-generic.122178.crash

Can some kind reader tell me how to retrieve the menus?
Thanks
Phil

---

### Post by deadflowr on 2018-07-26
nvidia-304 is not supported on 18.04.
nvidia has stopped supporting it for the more recent kernels.
(it should still work on older releases of Ubuntu that run older kernels and X stacks))

You can read my post from earlier and enigma9o7's found solution here:
[https://ubuntuforums.org/showthread.php?t=2395766&p=13783513#post13783513]("https://ubuntuforums.org/showthread.php?t=2395766&p=13783513#post13783513")

**Edit:** sorry, getting ahead of myself there. 
Per the menu issue though.
Can't you right click on the panel to get the Panel> option?
Then the Add new item option?

---

### Post by ajgreeny on 2018-07-26
There at least two menu applet items available to add from a right click in the panel -> "Add new items"; there is an **Applications menu,** not in the panel as default, and the **Whisker menu** which is there when you install.

---

### Post by khPWXxF on 2018-07-27
Many thanks both.
If I were to buy a new graphics card, what would you recommend?  I'm not a game player - just want TV.  Mythtv is best supported with Nvidia.  The 700 series is described as legacy -   so the next step up is a 1030?
Regards
Phil

---

