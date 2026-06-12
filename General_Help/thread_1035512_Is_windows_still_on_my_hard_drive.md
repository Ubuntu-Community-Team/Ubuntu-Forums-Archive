---
title: "Is windows still on my hard drive?"
date: 2009-01-09
forum: General Help
---

### Post by d1sc0rd on 2009-01-09
I recently installed ubuntu from an ISO image I downloaded off the website.  The installation went fine until it asked me to partition my hard drive. I used the default settings for resizing, but the process stayed at 1% for about an hour and I rebooted. When i re-did the installation, it installed on 100% of the hard drive.  I'm not sure if this is 100% of the partition, or of the entire disk. Now when I go to the GRUB menu on startup there are two ubuntu kernels, but no Windows.
-Is Windows still there?
-Is my hard drive partitioned?
-If so, how do I boot windows?

Any help is appreciated.
     -Ben

---

### Post by taurus on 2009-01-09
Let's see what happens to your harddrive.  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number one.

---

### Post by d1sc0rd on 2009-01-09
Thanks for quick response.

OK, Heres what I get in the terminal:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b668b66

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

---

### Post by taurus on 2009-01-09
Looks like you have killed your windows on your 250GB harddrive.  In other words, you told the installer to use the whole harddrive so Ubuntu uses the whole harddrive.

---

### Post by d1sc0rd on 2009-01-09
Is there a way to re-partition it then for windows? 

Or would I be stuck paying?:confused:

---

### Post by taurus on 2009-01-09
You mean recovery windows on that harddrive?  Unfortunately, I don't think you can bring windows back but perhaps you can recover some files on it.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

