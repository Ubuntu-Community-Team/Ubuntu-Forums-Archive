---
title: "A few questions about partitions"
date: 2006-03-31
forum: Desktop Environments
---

### Post by ELD on 2006-03-31
Okay heres a few n00b ones for you :)

I have a second hard drive formatted to fat32 can linux defualty read/write to this i know it can do fat but i wasn't sure if it meant fat32 as well?

If it can how can i mount that drive and get it to stay mounted (auto-mount on startup or something)?

Thanks.

---

### Post by krakan on 2006-03-31
Yes it can read/write form/to it it, just use -t vfat in your mount command..

If you want it mounted automatically when you boot then include it in /etc/fstab and put auto in the options field.. You'll be able to see from the existing entries in there what format to use, just remember that if you do det itto mount automatically then it'll try every time you boot, even if the drive is missing..

---

### Post by localzuk on 2006-03-31
Well to answer your first question: yes.

To answer the second, alter your /etc/fstab file to contain a line such as:
```

/dev/hdb1     /media/win_c    vfat    auto,rw,user      0     0
```

Obviously, change /dev/hdb1 to whichever drive/partition it actually is that you wish to mount. Also, change /media/win_c to the directory you wish to mount it to (this has to exist before you mount to it - so create it if it doesn't already).

---

### Post by ELD on 2006-03-31
Thanks guys ill give it a try in a bit :)

---

### Post by ELD on 2006-04-04
Okay another question how do i view the partition table to see where my disk is that i need?

Thanks.

---

### Post by earobinson on 2006-04-04
```
sudo fdisk -l
```

---

### Post by larsemil on 2006-04-04
[QUOTE=ELD]Okay another question how do i view the partition table to see where my disk is that i need?

Thanks.[/QUOTE]

if u know wich disk then just fdisk /dev/hdb and then show the partitiontable

---

### Post by ELD on 2006-04-04
Brilliant cheers guys, got access to my work, website, music etc nice one!

I take it that it will still be there when i eventually update to dapper when it comes out or would i need to re-mount it?

---

### Post by earobinson on 2006-04-04
AFAIK it will still be there but even if you do need to remount it you now know how!

---

