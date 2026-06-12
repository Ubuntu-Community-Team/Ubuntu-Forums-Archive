---
title: "updates break xorg legacy nvidia?"
date: 2005-12-15
forum: Desktop Environments
---

### Post by Jazman on 2005-12-15
12/15/05
I just used Update Manager to update my system.  Upon rebooting my system does not boot up the nvidia video legacy driver.  I changed the "nvidia" to "nv" in xorg.conf to get the video back.  After looking around in the /var/log/dpkg.log I found out that the following programs were upgraded:
(snip from dpkg.log) 
upgrade easytag 1.99.7-1build2 1.99.10-1~breezy1
upgrade gthumb 3:2.6.5-1ubuntu3 3:2.7.1-0ubuntu1~breezy1
upgrade libtotem-plparser0 1.2.0-0ubuntu3 1.2.1-0ubuntu1~breezy1
upgrade sbackup 0.8-1 0.9-1~breezy1
upgrade tomboy 0.3.2-9ubuntu4 0.3.3-2ubuntu1~breezy1
upgrade totem 1.2.0-0ubuntu3 1.2.1-0ubuntu1~breezy1
upgrade totem-xine 1.2.0-0ubuntu3 1.2.1-0ubuntu1~breezy1

I tend to think the totem & totem-xine upgrades may be the problem.  Is there a rollback I can use to restore the orginial upgrades and get the nvidia module back?  Where to look and start?

---

### Post by Jazman on 2005-12-16
12/16/05 followup
After poking around I noticed that the kernel was updated and so the problem is not the totem or totem-xine programs.
Seems to be related to be legacy nvidia and the linux restricted stuff of which there are plenty of messages on the forms.

---

### Post by Sico on 2005-12-17
Try this, worked for me:

[http://ubuntuforums.org/showthread.php?p=583728](http://ubuntuforums.org/showthread.php?p=583728)

---

