---
title: "Disk Space problem"
date: 2013-01-21
forum: Desktop Environments
---

### Post by raunhar on 2013-01-21
I had alloted 12GB to Ubuntu on my laptop. This was done about three years ago.
Now only 1.5GB is left.
I have all the files in other disk. The drive with Ubuntu has only the basic softwares.

While upgrading, low disk space error was continously popping up.
How do i create more space.

---

### Post by whatthefunk on 2013-01-21
Before doing anything, I would first backup your important data.

Have you ever used BleachBit?  It does a pretty good job of cleaning old un-needed packages and clearing out space.  If youve never run it and have had the same install for three years, I bet you can clear up quite a lot.

You also might want to try to see where the 10.5 GB is.  You can use xdiskusage for this.  

Both programs are in the software center.

---

### Post by Bucky Ball on 2013-01-21
Insert the LiveCD, launch Gparted when you get to the desktop, right click and unmount all partitions if they aren't already, shrink the partition next to the Ubuntu partition (/) and expand the Ubuntu partition (/) into the free space you have created.

If all your personal data is on another disk then you should be fine.

---

### Post by ajgreeny on 2013-01-21
If all your figures are correct, you have a problem of some sort which needs looking into.

However before doing anything, more details are needed.

[LIST=1]
[*]Is this a partitioned installation or carried out using wubi, ie, inside a windows installation?
[*]How long has it been installed for; the longer you have been using it the longer time there has been for some of the system folders, such as /var, to fill up. However, 12GB should be enough for most uses. I have a 10.04 system with the root partition which is the equivalent of your 12GB, managing perfectly in 10GB, and it still only takes 4.6GB of that 10 after nearly three years.
[*]Can you show us the output of ```
sudo fdisk -l
```and ```
df -hT
```one by one.
[*]What extra packages have you installed, or has it mainly been upgrades?
[/LIST]

---

