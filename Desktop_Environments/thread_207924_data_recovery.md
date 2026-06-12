---
title: "data recovery"
date: 2006-07-02
forum: Desktop Environments
---

### Post by buckets on 2006-07-02
i am new to linux and first installed suse 10.1 on my desktop.  My desktop has two hard drives one 60gig and one 40gig.  The 40 gig one is for my OS and the other for my files.  However, when i installed suse (i am now on ubuntu) i think it formated the hard drive or deleted the partition table on the second drive even though i only checked the 40gig one to install on.  can anyone help me recover my files?

---

### Post by yager on 2006-07-16
Please post the contents of your /etc/fstab file so we can see if you are mounting both drives.  It is possible the drive is sitting there and has not been mounted automatically.

BTW go to System>Adminstration>Disks and look at all of the drives in your system.  If you look at the Partitions tab for each hard drive, it will tell you where it is mounting to if it is mounted.  If the drive is mounted, navigate to that folder in the file browser to see if your files are still present.

---

### Post by Oddvar on 2006-07-16
I dont know if this help, but I had problems with my harddisk. I managed to make backup and save many of my files by using Knoppix.Reboot from a Knoppix CD, and maybe you find your files.

---

