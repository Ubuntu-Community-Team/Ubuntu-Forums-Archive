---
title: "NTFS partition problem"
date: 2009-02-15
forum: General Help
---

### Post by mad_max0204 on 2009-02-15
Hi

I have a added a hdd to my computer some days ago.
Its a 1.5tb hdd that I used to transfer some data and now I want to use it in my computer.
There were 2 ntfs partitions on it. I deleted first one and tried to install osx86 at my friends computer without touching the second partition (ntfs one with data).
Osx installation changed mbr and now, when hdd is in my computer I cant open that ntfs partition with data.
gparted says its unknown and I tried to fix it with ntfsprogs.
How can I fix this problem, even delete mbr from the hard drive and format the first part of the drive with ext3 and transfer data from that unknown ntfs partition to it so I can delete ntfs partition.
I dont have windows on my computer.

Thanks

---

### Post by Dies on 2009-02-15
Please post the output from 

```
sudo fdisk -ls
```

---

### Post by mad_max0204 on 2009-02-15
The partition is not shown with fdisk list.

partition is on sdd as sdd4

---

### Post by Dies on 2009-02-15
> **mad_max0204 said:**
> The partition is not shown with fdisk list.

partition is on sdd as sdd4

That's not the info I requested...


Good luck with your problem though.

---

