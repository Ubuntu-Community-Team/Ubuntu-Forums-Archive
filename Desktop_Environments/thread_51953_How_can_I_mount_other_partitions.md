---
title: "How can I mount other partitions?"
date: 2005-07-25
forum: Desktop Environments
---

### Post by retsel on 2005-07-25
I'm running Kubuntu dual booted with W98. From Kubuntu I'd like to access other partitions than the one where the Kubuntu files are. Kubuntu is on hda3, and it is mounted. The one I'd especially like to get to is hda5. It is shown as a hard drive along with hda3 and others. When I try to mount hda5 it won't do it - says it can't find something it needs in /etc/fstab or /etc/mtab. I've tried messing with both of those files, but have had no success in getting it to mount. Any suggestions would be appreciated.

---

### Post by nevarlen on 2005-07-25
Just mounted my other drives, so why not share it.. I have XP(ntfs) installed on hda1 and my document partiton(fat style so I could read/write easily) on hda7. 
My /etc/fstab looks like:

/dev/hda1       /mnt/xp         ntfs    ro,umask=0222   0       0
/dev/hda7       /mnt/common     vfat    umask=0,iocharset=iso8859-1,codepage=850,defaults       1       1

once you add the above lines to your /etc/fstab (of course, you may have to modify it to your needs, like hdaX, and so on)...just run "mount -a"
hope this helps

---

### Post by retsel on 2005-07-25
I tried making the changes you suggested, and it still won't mount. It says it needs something in the mtab file. Waht does your /etc/mtab file look like?

---

### Post by jasmuz on 2005-07-26
Read about it here:

[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

---

### Post by retsel on 2005-07-26
Thanks for your help! I got the information I needed.

---

