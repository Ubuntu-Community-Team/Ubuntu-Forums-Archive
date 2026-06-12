---
title: "&quot;Missing operating system&quot; after resizing"
date: 2009-04-28
forum: General Help
---

### Post by N_Nick on 2009-04-28
Moved from Apple Users area.

So i decided to resize my Ubuntu partition and upon reboot i get the "Missing operating system" message. I guess grub is **** up :/

All the files are there - i mounted /dev/sda3 using the LiveCD.

Is this a grub issue? And if so how do i fix it? 

Cheers.

PS: Heres the output of fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       20049   160838772+  af  Unknown
/dev/sda3   *       20050       23973    31519530   83  Linux
/dev/sda4           23974       24321     2795310   82  Linux swap / Solaris
```

Below are the tasks i performed with gparted.

Thanks for any replies.

---

### Post by freonchill on 2009-04-28
last time i "grew" a partition in gpartd it screwed it up

figured it was my own fault for not backing up the data before doing it (as it warns you should do) luckally it was a new ubuntu install so i only lost the configuration of a day or two when configuring ubuntu 8.04 for the first time.

---

### Post by N_Nick on 2009-04-28
No data were lost in my case, its all there - I just can't boot

**Edit: catlett's tutorial didn't work for me at first.  Tried again after a reboot and worked like a charm.**

> [http://ubuntuforums.org/showthread.php?t=224351&highlight=missing+operating+system](http://ubuntuforums.org/showthread.php?t=224351&highlight=missing+operating+system)

---

