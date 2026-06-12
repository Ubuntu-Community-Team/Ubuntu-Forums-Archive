---
title: "fsck problem???"
date: 2009-02-04
forum: General Help
---

### Post by Mostly Harmless on 2009-02-04
While trying to boot up recently, my computer ran fsck and told me to run fsck manually. When asked for the root password I supplied the password of my account, which is an administrator. I was then told the password was incorrect. I did give the root account a password, which I then reset with the random password feature because I didn't want anyone guessing it and gaining access to my computer. I am now completely locked out. Please help. (Running ubuntu 8.10, if relevant)

---

### Post by taurus on 2009-02-04
Boot with the LiveCD.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo fsck */dev/sda1*
```
Or whatever the partition your root filesystem, /, is.

---

### Post by Mostly Harmless on 2009-02-04
sudo fsck /dev/sda1 gives me 
> fsck 1.41.3 (12-Oct-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 15893 files, 1000965/1114419 clusters
and I get a slightly different (says filesytstem contains errors, not has been mounted 32 times without being checked) message from fsck

---

### Post by taurus on 2009-02-04
/dev/sda1 is your not root filesystem.  Do you really want to run fsck on a fat32 filesystem?


```
sudo fdisk -l
```

---

### Post by Mostly Harmless on 2009-02-04
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1111     8924076    c  W95 FAT32 (LBA)
/dev/sda2   *        1112       24321   186434325    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x2427493d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10337    78147688+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6df10dc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

---

### Post by taurus on 2009-02-04
Did you install Ubuntu using wubi?

---

### Post by Mostly Harmless on 2009-02-04
A friend of mine installed ubuntu for me. Is there any way I could tell how it was installed?

---

### Post by taurus on 2009-02-04
I don't see any Linux filesystem and swap partition so your friend either installed it using wubi or he/she used fat32/ntfs filesystem which is a big no-no.  Maybe it's time you call your friend up and ask.

---

### Post by Mostly Harmless on 2009-02-04
What would I need to do in either situation?

---

### Post by Mostly Harmless on 2009-02-04
Help?!?! I emailed my friend but I need this up and running ASAP so I can get some important files off it!

---

### Post by Mostly Harmless on 2009-02-04
Just got reply, he says he used the Live CD with all the default options

---

