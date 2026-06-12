---
title: "gnome desktop meltdown , help. gnome is confused as to what my root password is"
date: 2007-07-03
forum: Desktop Environments
---

### Post by recon69 on 2007-07-03
my ubuntu gnome desktop has developed some serious problems.
I was using it to day when my gnome seemed to lock up, I could get around the menus but no programs would start and i could not shut the system down. so I cut the power to reboot, and my desktop now has serious problems.All the admin programs fail to run reporting an invalid password that i know is correct. the desktop is all funny, colors are different , the keyboard does not repeat when a key is held down and lots of other strange stuff. 

mec@mec-desktop:/usr/sbin$ sudo update-manager
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

I get this when i use the gui to start "update manager" or "User and Groups"
"Failed to run /usr/bin/update-manager as user root:
 Wrong password."

error when update manager tries to update 
E: /var/cache/apt/archives/libkrb53_1.4.3-5ubuntu0.4_i386.deb: unable to open files list file for package `libdbus-1-2' 

anyone got any idea what wrong or how to fix it ?

thx

---

### Post by lisati on 2007-07-03
That's one of the hazards of doing the contemporary equivalent of "flicking the big red switch" (using the power switch to force a shut-down) - sometimes the settings get messed up because the OS doesn't have a proper chance to keep its notes up-to-date.

As to a solution: The alternate CD for Ubuntu 7.04 has a "repair broken system" option. You might want to try that........

---

### Post by recon69 on 2007-07-03
well, I did try the proper way, but my system was unresponsive so could not really think of any other way of shutting it down. but my bad for hitting the big red button. 

I will try install 7.04, probably about time i did a upgrade

---

