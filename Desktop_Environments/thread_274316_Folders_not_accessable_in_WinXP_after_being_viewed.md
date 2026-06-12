---
title: "Folders not accessable in WinXP after being viewed in Ubuntu Live"
date: 2006-10-09
forum: Desktop Environments
---

### Post by xcaliber219 on 2006-10-09
I have an external USB harddrive that has its entire space dedicated to an NTFS partition.  I have a bunch of stuff on the drive that I use when I'm in Windows XP.  I put in the Ubuntu Live disc (version 5.10) to see how the OS looked (quite nice).  It picked up and placed the usbdrive on the desktop.  Now, a couple of my folders on the external drive have images in them.  I decided to view those images with I think GView.  There are only two image viewers on the live CD.  Anyway, now I'm back in Windows XP and I can't access those folders.  It says Permission Denied.  What's the issue?

---

### Post by kidders on 2006-10-09
Hi there,

Unless you've tweaked Ubuntu to grant you read/write access to NTFS partitions, this is nothing more than a strage coincidence, I'm afraid. Under normal conditions, Ubuntu can't write to NTFS filesystems, so it wouldn't have been physically able to alter anything.

Are you sure there isn't another explanation? Do the ACLs for the inaccessible folders seem reasonable?

---

### Post by xcaliber219 on 2006-10-09
What happened was Ubuntu took ownership of the folders.  I had to dive deeper into winXP admin stuff but I was able to fix it.

[http://www.le.ac.uk/cc/dsss/docs/acls2.shtml](http://www.le.ac.uk/cc/dsss/docs/acls2.shtml)

---

