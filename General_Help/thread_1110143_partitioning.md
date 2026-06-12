---
title: "partitioning"
date: 2009-03-29
forum: General Help
---

### Post by bradpurvis on 2009-03-29
is there a way i can do it while in ubuntu? i need to dual boot xp/vista and i don't want to have to reinstall ubuntu

---

### Post by SuperSonic4 on 2009-03-29
You can't do it from hard drive ubuntu because the drives need to be unmounted. You can, however, resize it using gparted on the ubuntu live cd but as usual with partitioning backup any data you can't afford to lose

---

### Post by bradpurvis on 2009-03-29
is resizing the same thing as making a new partition? Becuase I really need to  install windows

---

### Post by SuperSonic4 on 2009-03-29
No, resizing is taking off space at the end of the parition which should leave everything in tact, reducing free space on ubuntu in which you'd install windows

---

### Post by bradpurvis on 2009-03-29
one last question, where is gparted?

---

### Post by bradpurvis on 2009-03-29
BUMP hello?

---

### Post by koanhead on 2009-03-29
gparted is on the install cd but afaik it is not installed by default. On an installed system you can get Partition Editor via Synaptic or by doing:

sudo apt-get install gparted

If gparted is the same as the gui-based Partition Editor then its launcher will be in the System->Administration menu. That's where mine is anyway.

---

### Post by bradpurvis on 2009-03-29
so does that mean i can partition it while in ubuntu?

---

### Post by Chemical Imbalance on 2009-03-29
No, as has been said, you need to boot to a live environment so that you're harddisk is not mounted.  You should never partition a mounted drive.

Boot the Ubuntu cd into a live session and then go to System, Administration, Partition Editor

Be careful with partitioning:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Also, it is recommended that you install Windows before linux, because Windows wipes your GRUB bootloader with its own bootloader.
You will have to boot another live session with Ubuntu to reinstall GRUB after Windows installs.

---

