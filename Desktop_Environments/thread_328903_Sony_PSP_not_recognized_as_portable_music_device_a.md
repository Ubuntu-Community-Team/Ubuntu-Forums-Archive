---
title: "Sony PSP not recognized as portable music device after FW update"
date: 2006-12-31
forum: Desktop Environments
---

### Post by jweb on 2006-12-31
When I first connected my Sony PSP via USB to my laptop running Ubuntu 6.10, I was happy to see that it was immediately recognized as a portable music device and auto-mounted as such (with the iPod icon).  Everything worked great (transfer of files through folders, through Amarok, etc.)  I upgraded the firmware of the PSP and, now, Ubuntu still recognizes the device and automounts it, but as a standard "usbdisk" (to /media/usbdisk) and not to the mount point I previously had (/media/psp). 

I don't really know where to look to understand why.  I did some searching and I suppose it has something to do with udev mounting rules and the fact that Ubunut might have been using something related to the firmware version as a mounting rule, but I couldn't find anything in /etc/udev/rules.d. 

Any suggestions?

Thanks in advance...

---

