---
title: "How to enable SWAP partition once switched off for resizing"
date: 2008-05-17
forum: Desktop Environments
---

### Post by squiggly_crayon on 2008-05-17
I had switched off the SWAP using QTparted for resizing of the Linux partition. Since then, I tried using QTparted gui option to enable swap and swapon -a also, but it seems to give me an error.

swapon -a

error:
swapon: cannot canonicalize /dev/disk/by-uuid/c38d7080-bf3f-4734-81e7-9ec7c532d389: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/c38d7080-bf3f-4734-81e7-9ec7c532d389: No such file or directory

While i have 1.5 GB ram, I do not face trouble in using the laptop, I cant use the hibernation mode etc.Please help.

thnx in advance

---

### Post by Patb on 2008-05-18
Squiggly, is the uuid correct for the swap partition? To check:
```
sudo blkid
```

If it is wrong you may need to edit your fstab file:
```
gksudo gedit /etc/fstab
```
Cheers, Pat.

---

### Post by squiggly_crayon on 2008-05-18
thanks Pat
it worked like a charm
quite silly of me to ignore this possibility

---

### Post by kindofabuzz on 2008-05-19
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

also shows you how to make a swap file instead of a dedicated partition.  a swap file is just as fast as a swap partition with the 2.6 kernel.

---

