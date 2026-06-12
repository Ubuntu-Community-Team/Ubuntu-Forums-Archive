---
title: "on startup linux send me to initramfs"
date: 2011-05-31
forum: Desktop Environments
---

### Post by rizos on 2011-05-31
some how i mess with fstab (don't know how or what as it was last thing i was "editing")


all started when added a used hard drive to my system...


now i have 20gb extrabox (new hard drive), 180gb with 2 partitions one windows 7 the second linux natty. and an extra partition for using windows/linux sharing files 20gb.

been trying to add my new hard drive to mount point and some how i mess terribly fstab deleting swap space.

then use gparted to enable 2gb after liniux partition of swap space... (2 more gb of unallocated space after windows partition and before linux partition that i dont know what happened there :()

reboot and now after booting selecting linux or linux recovey mode send me to initramfs prompt and cant do nothing from there.

i can access my windows 7 partition but with some issues mainly too slow (guess is out of space) 

but i cant access /sdb5 where my linux partition is.

i try with linux puppy and i cant mount sdb5 at all...but all the other partitions it¿s possible.


i try the livecd natty and says it must delete the entire disk


i don't know what to do to reestablish fstab to how it was before.


any ideas on what and how to do it?


thanx a lot.

---

### Post by prshah on 2011-05-31
> **rizos said:**
> some how i mess with fstab 

Please boot off a live CD (or Puppy) and post back the output from the following commands to help restore your fstab.```
sudo fdisk -l
``` (In puppy, use "root terminal" instead of ordinary "terminal").

This will list your connected hard drives, partitions and other information. Based on this, we can offer more advise.

The "problem" is relatively easy to fix, but more information is required.

---

### Post by rizos on 2011-05-31
this is my infamous hard drivesinfo wont be surprised if is messy...i been trying to fix it with no success...

thanx!...


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2483    19937248+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xafe6fd0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *          13        5839    46793727+   7  HPFS/NTFS
/dev/sdb3           15808       19457    29312000    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sdb4            6165       15807    77453184+   5  Extended
/dev/sdb5            6165       15517    75123712   83  Linux
/dev/sdb6           15

---

### Post by rizos on 2011-06-08
no one?

---

### Post by prshah on 2011-06-08
> **rizos said:**
> Disk /dev/sdb: 160.0 GB, 160041885696 bytes
/dev/sdb5            6165       15517    75123712   83  Linux
/dev/sdb6           15

This information is incomplete. Can you please post the complete output?

Can you also post your /etc/fstab (most likely your linux partition is /dev/sdb5). Please post back if you cannot access your /etc/fstab and need details.

---

### Post by rizos on 2011-06-14
im sorry for incomplere info didnt notice.


now my info changed a lot because i lost all my info and no computer last days.


i open a new thread with my new "situation".


thanx anyway.

---

### Post by ionplay on 2012-02-03
no resolution here either???

why does Ubuntu boot to initramfs after a fresh install - how can it install and then not boot????

---

