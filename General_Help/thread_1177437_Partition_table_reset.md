---
title: "Partition table reset"
date: 2009-06-03
forum: General Help
---

### Post by MimziM on 2009-06-03
I need to reset my partition table without losing 1 of the data partitions???
Any help?

---

### Post by Entropy_Sam on 2009-06-03
> **MimziM said:**
> I need to reset my partition table without losing 1 of the data partitions???
Any help?
 
 
Aside from moving the data to another drive or backing it up onto a CD, I don't think it's possible - sorry.

---

### Post by MimziM on 2009-06-03
This is alot of data its a 300gb partition. I'm using ubuntu off the install disk at the moment and i can see it and use files from it, but when i go to install eithere I can't because I cant slect a device, cos there are none. Or if I try install from boot I only have the option to create a new partition tree, but that will destroy everything.
Moving it to another drive is of course the  best option but I don't have  that much space anywhere else. There's got to be a way. Even in windows(spit) it can be done ....?

---

### Post by Entropy_Sam on 2009-06-03
How is/are your hard drive(s) partitioned? If you could give a detailed breakdown of partitions with their sizes, current usage and intended usage we might be able to offer more help. You should be able to install without creating a new partition table.

---

### Post by MimziM on 2009-06-03
mypartition table is messed from fro multiple experimental installations. The one that did it was  Fedora(10gb partition). I was able to install Mandriva(10gb partition) after that and couldnt boot into the fedora but could mount the drive and veiw files in mandriva.
There is also a 2gb swap partition, the 300gb data partition and 670gb free space.
I just want to keep the data partition,

---

### Post by VMC on 2009-06-03
```
sudo fdisk -l
``` this gives partition table information. So what's the output of that command?

---

### Post by Entropy_Sam on 2009-06-03
Part of your problem may lie in the fact that a given hard disk is only allowed 4 primary partitions and 2 extended partitions. I've probably got the terminology a little wrong there, but no matter.

Running GParted (System->Administration->Partition Editor) in Ubuntu from a LiveCD, select and delete the two 10Gb partitions, then Create 1 or 2 ext3 partitions in the newly-created free space, reboot and install Ubuntu there (manually select it from the installation program and assign it as root ("/").

Same partition table, modified! :-)

---

### Post by MimziM on 2009-06-03
Unable to seek on /dev/sda

---

### Post by VMC on 2009-06-03
Try booting with a livecd and run **fsck** against the hard drive.

---

### Post by MimziM on 2009-06-03
My partition editor says the whole hdisk931.51GB is unallocated

In my places I can veiw files from 300gb data and only one 10gb partition(

---

