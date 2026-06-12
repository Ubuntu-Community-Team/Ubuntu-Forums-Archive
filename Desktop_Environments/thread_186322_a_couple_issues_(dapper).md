---
title: "a couple issues (dapper)"
date: 2006-06-01
forum: Desktop Environments
---

### Post by n_hendrick on 2006-06-01
I enabled ntfs write support on a local disk using the following how-to:

[http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481)

and now I have a tag in the tab to the left of the filemanager (nautilus) that won't allow access of the drive. I have to scroll down and manually enter media/hda1 to gain access. Also I cannot change the drive through nautilus I have to go through it as root using a terminal. Which is strange because I have it set for the main user group and user name. The error I get when I try to access the drive through the tab is apparently mtab related...it says drive already mounted through fstab. Originally I could access the drive through the tab although the name of the tab changed from "hda1" to "59.1GB Volume" when I enabled ntfs write support.  I want to be able to access the drive through the new tab, and change the drive contents using nautilus. 

on a side note, I am also trying to get my gravis joystick working...There is no related js0 device in dev or dev/input...I can't even recreate the device now using MAKEDEV whick I could in breezy. Any ideas...I use this joystick in zsnes. There has to be a way to create the js0 in dapper, and reboot to get the joystick working...It'd be nice if I didn't have to reboot to get the js0 detected, there has to be a work around, but If I could just get it detected on a reboot that would suffice.

Other than those two issues, dapper is running awesome, I did a apt-get dist-upgrade and had no issues, way to go Ubuntu!

---

