---
title: "USB HDD Permissions"
date: 2007-07-20
forum: Dell  Ubuntu Support
---

### Post by teotwawki on 2007-07-20
I've installed Feisty 7.04 on my E521 and have a WD USB external HDD formated under Windows XP as an NTFS drive. Ubuntu detects the drive when it is connected and I can access all files but the drive is mounted read-only. fstab shows the device is to be mounted rw however. I can't seem to change permissions using sudo chmod. Any ideas?

Thanks in advance...

---

### Post by yabbadabbadont on 2007-07-20
Read through [this](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971) and see if it helps.  If you have any questions afterwards, please post them back here.

---

### Post by teotwawki on 2007-07-20
Yes, I found the solution there. Thanks! I'm a ubuntu/linux newbie. I'll look through the Community Docs before asking simple questions again. Nice resource you all have set up here...

---

### Post by pbcartwright on 2007-07-20
I have a WD Mybook 500Gb drive also. I use it to back up my laptop ( XP/Gutsy dual boot) and my desktop ( SUSE 10.2).
the first thing I did was reformat it ext3. Now I can write to it without a problem in Windows and Linux.
there are a number of tools you can use to reformnat it.. gparted, cfdisk...

---

