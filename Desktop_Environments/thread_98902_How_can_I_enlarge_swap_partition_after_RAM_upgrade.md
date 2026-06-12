---
title: "How can I enlarge swap partition after RAM upgrade?"
date: 2005-12-04
forum: Desktop Environments
---

### Post by avilella on 2005-12-04
Hi all,

I recently upgraded a desktop computer from 1GB to 4GB RAM.

As I installed Hoary on it when it had 1GB, the swap is of 2.5GB, which I asume is 2.5x the RAM detected at install time:

SwapTotal:     2650684 kB

I would like to enlarge the swap according to the new RAM size I have, which I suppose would be 2.5x4GB = 10GB

I reckon there should be an easy and clean way to do it via LVM or something similar, but I haven't found out how by myself.

Anyone?

Thanks in advance,

    Albert.

---

### Post by ScreemingBlue on 2005-12-04
Try booting off the Ubuntu LiveCD and using the GParted tool to resize your Swap partition.

---

### Post by FLeiXiuS on 2005-12-04
Once you get a GIG of ram, it's very unlikely you'll need 2.5GB swap space.  I have a gig ram / gig swap.  The swap is never touched.  


In case you do want to enlarge it.  Depending on where it's placed and how much freespace is available.  You can safely:
```

$ sudo swapoff -a
$ sudo cfdisk YOUR/HARD/DRIVE
```
Example: $ sudo cfdisk /dev/hda

Make the necesary changes...save then exit.

```
$ sudo mkswap /dev/swap/location
```
Replace /dev/swap/location with the location on your hard drive where you create the swap partition.

```
$ sudo swapon -a
```
This should activate it, then your good to go.

---

### Post by mckemie on 2005-12-04
I agree that you are highly unlikely to need, or will be able to use, a larger swap partition just because you added ram.

An easy way to add swap is with a swap file, rather than a swap partition.  "man mkswap" tells you all about it.  You can use the swap file in conjunction with your "normal" swap partition.

---

### Post by avilella on 2005-12-04
[QUOTE=mckemie]I agree that you are highly unlikely to need, or will be able to use, a larger swap partition just because you added ram.
[/QUOTE]

It is worth to say that the RAM is needed not for normal Desktop-related apps but for a software project that can easily consume 4GB on normal execution and peak at 8-10GB sometimes.

---

### Post by az on 2005-12-04
[QUOTE=avilella]It is worth to say that the RAM is needed not for normal Desktop-related apps but for a software project that can easily consume 4GB on normal execution and peak at 8-10GB sometimes.[/QUOTE]
Holly Moley!

I suspend-to-disk my desktop system.  Thqat requires that the contents of ram be cached to the swap partition.  You need to have a swap partition at least 25 percent larger than your ram to do this.

This may or may not be relevant to you.

How are your partitions lain out?  You can shrink a partition from it's end, but not it's beginning.  You may have to shrink the partition which preceeds your current swap, delete your swap and recreate it starting at the earlier spot.

To use Gparted from the live cd, you need to swapoff your swap, since it uses it by default.

You can always boot the installer cd and use parted from a virtual console (CTRL-ALT-F2 - once hardware detection has taken place and the installer components (includeing parted) are loaded)

---

