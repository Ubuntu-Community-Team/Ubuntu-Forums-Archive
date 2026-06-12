---
title: "See Ubuntu partition w/ new Ubuntu"
date: 2006-10-04
forum: Desktop Environments
---

### Post by SLP on 2006-10-04
OK...so I just Installed a new Ubuntu in a new partition.:-D 

and I have this old ubuntu in a completely different partition and different harddrive. and I want to get into the old ubuntu and get all my files...


how do I do this????

---

### Post by jmerlin on 2006-10-04
You can manually mount it to a new directory or you can add it to your fstab file ( /etc/fstab ) to automatically mount it everytime your system boots up.

An example to a harddisk partition mount:

mount -t ext3 -o defaults,errors=remount-ro /dev/hda2 /ubuntu2/

Where /ubuntu2/ is the new root dir for the other install partition.

man mount
man fstab

enjoy.

---

### Post by SLP on 2006-10-05
/dev/hdd5 is already mounted or /media/ubuntu2 is busy :confused: 

then i try to unmount /dev/hdd5 and syas its not mounted

what next???

---

