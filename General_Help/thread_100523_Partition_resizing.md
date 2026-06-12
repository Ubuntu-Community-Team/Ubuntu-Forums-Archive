---
title: "Partition resizing ?"
date: 2005-12-07
forum: General Help
---

### Post by Bachstelze on 2005-12-07
here is my fdisk -l :

```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1265    10161081   83  Linux
/dev/hda2            1266        4864    28908967+   5  Extended
/dev/hda5            1266        1387      979933+  82  Linux swap / Solaris
/dev/hda6            1388        4864    27928971   83  Linux

```

So, the /dev/hda1 partition is my / partition and is about 10 GB with half of it used. I thought I should give a try to other distros without messing up my well-configured Ubuntu system so I would like to resize it to, say, 6 GB and have 4 GB for a new distro. Well, fair enough, I put my Knoppix CD in the drive, boot and searched for the partitioning tool. I used "QTParted" but it won't let me resize my partitions even though everything is unmounted. Any ideas ? It is the only Live CD I have atm, I gave my Ubuntu one to a friend to try it out.

---

### Post by aysiu on 2005-12-07
I have never had a greyed-out option using Mandriva's DiskDrake.
I don't use Mandriva--just DiskDrake.
I pop in the first Mandriva installer CD and go through the partitioning process. Then I reboot.

QTParted and GParted are okay, but sometimes they just don't let you do stuff you should be able to do.

---

### Post by Bachstelze on 2005-12-07
I also have an old Mandrake 10.0 install CD, maybe it will work too. I'll try it out, thanks for the tip :)

---

