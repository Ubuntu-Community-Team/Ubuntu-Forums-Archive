---
title: "Can't find Gfloppy"
date: 2009-01-04
forum: General Help
---

### Post by Guns90 on 2009-01-04
High guys.  I've been away from ubuntu for a while, but I'm back (TO STAY).  

The last distro I used was 6.04, so some things are differant now. I did a clean install of the latest distro, 8.10.  I'm trying to reformat a sdhc card, but I can't find a way to do it.  The card mounts okay, but right clicking on it does not show the format option like it did in 6.04.  I can't find a floppy formatter in Applications, System, system tools, anywhere. A little help please?

---

### Post by homemadejam on 2009-01-04
I'd have ago at install Partition Manager... you should be able to find it in the Add/Remove programs.

Then you can select any drive or removable media, and partition it up, format etc.

Let me know if you have any problems with it.

Jam

---

### Post by linux_tech on 2009-01-04
Insert your memory card

In terminal check output of 
```
sudo fdisk -l
```
or you can also use 
```
df
```

(note device name of sd card) ie. /dev/sdf1

unmount the disk
type ```
umount /dev/sdf1  <--using appropriate device name
```
or right click on the sdhc on the desktop and choose unmount


then just type: 
```
mkfs.fstype /dev/sdf1 <--using appropriate device name 
```
ie.
mkfs.ext2, mkfs.ext3, mkfs.minix, mkfs.msdos, mkfs.vfat

-----------------------------------------------------------------------

or you can also use gparted to format the disk
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it with your card plugged.

gparted is also on live cd or you can install it, then use it
```
sudo apt-get install gparted
```
You should be able to find it-
system>administration>partition editor
then click Gparted on menu>Devices >select the sdhc device;
then right click on device, and choose format-to

---

