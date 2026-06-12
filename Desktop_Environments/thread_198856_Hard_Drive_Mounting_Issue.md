---
title: "Hard Drive Mounting Issue"
date: 2006-06-17
forum: Desktop Environments
---

### Post by Pooch on 2006-06-17
Hi,

I have 2 hard drives, one has the filesystem, and the other has been formatted and partitioned into ext3. I have mounted the hard drive, although no icon has appeared on the desktop, or in the Computer folder. I named the mounting folder HardDrive0 and made a link named HardDrive leading to the mount. Is there any way to make a mount appear on the Desktop in 6.06. (I did it in 5.10)

**My FStab Entry**
```
/dev/sdb1	/media/HardDrive0  ext3	defaults	0	0
```

---

### Post by Alpha_Cluster on 2006-06-17
You should be able to if you make the link to /media/HardDrive0

---

### Post by Pooch on 2006-06-17
I can, but its a regular shortcut, It automatically looked like a Hard Disk Icon before. It also showed up in the Computer folder.

**Edit:** A reboot solved the issue. For some reason mount -a didn't substitute a reboot.

---

