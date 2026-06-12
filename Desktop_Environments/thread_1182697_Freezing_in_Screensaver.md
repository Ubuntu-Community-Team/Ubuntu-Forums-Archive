---
title: "Freezing in Screensaver"
date: 2009-06-09
forum: Desktop Environments
---

### Post by chome4 on 2009-06-09
New to Ubuntu and the latest version.
 
When going into Screensaver Properties, It's not too long before the machine locks up. The mouse is OK but the machine requires a switch off and reboot.
 
Any ideas?

---

### Post by grikdog on 2009-06-16
> **chome4 said:**
> New to Ubuntu and the latest version.
 
When going into Screensaver Properties, It's not too long before the machine locks up. The mouse is OK but the machine requires a switch off and reboot.
 
Any ideas?
Yes, I've got the same problem, and no idea what causes it.  The only thing that seems to clear this up (for awhile) is turn swap off and on.  I use Administration -> Partition Editor for this.  DO NOT modify your partitions!  DO select the swap partition, then Partition -> Swapoff.  Same again, only this time Partition -> Swapon.  It's entirely possible this is just magic-wand-waving, but it seems to clear things up for a bit.  (I suspect the REAL issue is some kind of resource deadlock, and turning swap off just forces the system to clean up.)

If anyone has a better idea?

---

