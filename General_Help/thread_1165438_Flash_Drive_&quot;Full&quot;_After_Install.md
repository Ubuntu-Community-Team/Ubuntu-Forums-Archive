---
title: "Flash Drive &quot;Full&quot; After Install"
date: 2009-05-20
forum: General Help
---

### Post by Mrandoman on 2009-05-20
I recently wrote a .img onto my 1GB Sandisk Cruzer flash drive using dd. After deleting all the files on it (including hidden files), it shows that it only has about 467 MB out of the 1GB free. What's the problem with it?
Also, would "sudo -rm rf /dev/sbd1" fix it and only affect the flash drive?

---

### Post by danwood76 on 2009-05-20
What img file did you write to it?
If you wrote an image from a smaller disk then its possible the partition is smaller, obviously if it was a backup then this wont be the case.

sudo -rm rf /dev/sbd1 wouldnt do anything for you and could kill your OS.
Use something like gparted to repartition the drive.

---

### Post by Mrandoman on 2009-05-20
In gparted it shows it as being 1GB of unallocated space, while in properties, it says its formatted to MSDOS.

---

### Post by danwood76 on 2009-05-21
It sounds like you have DD'd a partition dump to the whole disk.
So you wont have a partition table anymore which will cause you problems.

In gparted create a new msdos partition table (device->create partition table) and a new partition (format it fat32), you should then have your whole drive back.
Obviously you will loose all data on the disk in doing this but you will get your whole disk back.

---

