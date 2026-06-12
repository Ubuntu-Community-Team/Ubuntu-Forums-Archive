---
title: "'Power manager still running' error on login"
date: 2010-05-11
forum: Desktop Environments
---

### Post by davosmith on 2010-05-11
Since upgrading to 10.04 (from 9.10) 2 days ago, I have been getting an error message whenever I log in.

It tells me that 'Power manager is still running' and gives me options of 'logout anyway' or 'cancel' (I'm writing this from memory, so may have got the wording slightly wrong). Clicking 'logout anyway', then continues with the login process, with no further problems (as an aside, I am running a desktop, so I'm not sure that Power Manager has much to do anyway...)

Anyone got any ideas?

---

### Post by ipadm on 2010-05-11
I have the same issue. Using DELL Inspiron 1501 (basing on AMD64, RAM 4Gb). 

It was some power management problem before so I was thinking it is usual only for my notebook.

---

### Post by exXP on 2010-05-11
I'm having a similar problem with my HP Pavilion (AMD Athlon II).  If I select 'Cancel' the screen freezes but the cursor can still be moved.  This requires a Reset. I also hear a fan come on during the initial boot stage. This goes off after a few seconds but the log- in problem stays.  After I select 'Log-off Anyway'  there is an agonizing wait of several seconds before normal service is resumed. My suspicion is that the nVidia driver is involved
exXp

---

### Post by ipadm on 2010-05-11
> **exXP said:**
> My suspicion is that the nVidia driver is involved
exXp

No, I have buildin ATI, so it is not nVidia problem.

---

### Post by exXP on 2010-05-12
This problem may be connected to Grub.  One of the things I played around with that involved Grub was bootchart. I've since uninstalled it which was about the time the problem started. If we can't find a cure I may do a complete reinstall.  Which is tedious but better than having the Power Management panel popping up each time I log on.  Incidentally, the log on procedure is a bit fragmented now with various images flashing on for a fraction of a second
exXP

---

### Post by exXP on 2010-05-12
This problem may be connected to Grub.  One of the things I played around with that involved Grub was bootchart. I've since uninstalled it which was about the time the problem started. If we can't find a cure I may do a complete reinstall.  Which is tedious but better than having the Power Management panel popping up each time I log on.  Incidentally, the log on procedure is a bit fragmented now with various images flashing on for a fraction of a second
exXP

---

### Post by NMahmood on 2010-05-30
> **exXP said:**
> This problem may be connected to Grub.  One of the things I played around with that involved Grub was bootchart. I've since uninstalled it which was about the time the problem started. If we can't find a cure I may do a complete reinstall.  Which is tedious but better than having the Power Management panel popping up each time I log on.  Incidentally, the log on procedure is a bit fragmented now with various images flashing on for a fraction of a second
exXP

I uninstalled GRUB2 with no luck. 

I did manage to fix it by logging in and changing the power settings in the power management utility, then restarting.
At one point I booted in recovery mode single user, but I doubt that jigged anything, I reckon it was bad information written to the power management tool by the update.

---

### Post by sciten on 2010-06-25
I had the same problem. The solution? Remove the installation CD! The message appears every time with the CD and never without. Also, the installation CD causes the same message to appear on an existing (and updated) Ubuntu 10.04 installation on the same Dell laptop.

---

### Post by hopikrishnan on 2010-07-06
After installing 10.04 over the 9.04 (fresh install) I had the system working perfectly.  I was even able to use my trackpad mouse without dicking around.  Then I got the urge to customize the login screen.  I did that with the use of ubuntu-tweak gui.  When I had the space-5 background and the old logo, I got the "Power Manager Still running" window on a fresh login.  Same problem that all others describe here !!  "logout anyway" was not the obvious first choice to continue with the logon ; but that is how it was.  Since I got into trouble with the tweaking of the login screen, I decided to try out another screen.  Voila..after switching to Jupiter, the "Power Manager Still Running" window does not come up anymore.  The login is still as slow as when I had the fresh install.  My system:
Sharp Laptop Actius AL27
AMD 64-2700 processor (using Ubuntu 10.04 AMD-64 version)
512MB RAM
dual boot with the default Grub version, Windows XP is the other OS

---

### Post by owennewo on 2010-07-08
You may want to look at this bug, there are some suggestions that may help you out:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862)

---

### Post by celev on 2010-07-28
Had the same problem when updating. It seemd to be the graphics card. Radeon HD in my case. power manager still running kept on poppin out at logon and the graphics were awful. it just happened out of nowhere. fglrxinfo wouldn't recognise the graphics anymore, so I reinstalled the driver. restarted and voila!. it worked. no more power manager still runnning messages at logon and the graphics came back.

---

### Post by power ohn on 2010-08-10
> **sciten said:**
> I had the same problem. The solution? Remove the installation CD! The message appears every time with the CD and never without. Also, the installation CD causes the same message to appear on an existing (and updated) Ubuntu 10.04 installation on the same Dell laptop.

Agreed, I had a CD (not the install CD just a blank one) in the drive of my Dell Studio desktop it caused a similar error. It also replaced the power button in the top right corner with "ohn" the last few letters of my login. Took out the CD and it was solved.

---

