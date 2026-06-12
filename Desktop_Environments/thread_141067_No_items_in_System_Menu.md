---
title: "No items in System:/ Menu"
date: 2006-03-07
forum: Desktop Environments
---

### Post by paulbarbee on 2006-03-07
I'm not sure how but I lost all items in System:/ Menu. I've been messing around with my KDE setup but this applies to all users. Nothing happens when I put in a CD-R. Gnome appears to work fine. I'd really like to access my media from KDE. 

Any ideas??

Thanks in advance to thiose who answer.

---

### Post by paulbarbee on 2006-03-07
Ok, I stubled across this thread. [http://ubuntuforums.org/showthread.php?t=49939](http://ubuntuforums.org/showthread.php?t=49939)

and discovered that some users had been misconfigured so that they couldn't acess CD's and Hal wasn't a member of cdrom, floppy or plugdev. I made hal a member of these groups, used Gnome's Users and Groups application and made all of theusers able to acess CD's, rebooted and now everything works.

Thanks again to anybody who was trying to come up with a solution.

---

