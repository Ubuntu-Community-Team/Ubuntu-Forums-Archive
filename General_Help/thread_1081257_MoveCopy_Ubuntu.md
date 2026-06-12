---
title: "Move/Copy Ubuntu"
date: 2009-02-26
forum: General Help
---

### Post by RedSingularity on 2009-02-26
Hey guys, can someone tell me how to move my ubuntu install to a new hard drive?  I just installed it (SATA) and i need the space so i would like to copy my install to it.

---

### Post by taurus on 2009-02-26
I think Clonezilla is what you need.  It can restore image from a smaller harddrive to a larger harddrive which I don't believe PartImage is able to do.

[http://www.clonezilla.org/](http://www.clonezilla.org/)

> 
Clonezilla is NOT able to restore the image from LARGE harddisk to smaller one, but it CAN restore the image from small harddisk to larger one. Three choices are available. Here they are:
Choice (1).
0. Save the image in the Clonezilla server.
1. Do a normal restoration to target machine by clonezilla.
2. When clone is finished, use gparted to resize or move the partition. You can install gparted in the DRBL server, then boot the client into remote-linux-gra (dcs -> remote-linux-gra) mode, login client as root, run gparted to do that. Or you can use gparted LiveCD or LiveUSB to do that. A gparted-clonezilla dual boot live CD is available, for more info, check [http://gparted.free.fr/GParted-Clonezilla/](http://gparted.free.fr/GParted-Clonezilla/) or [http://www.icewalkers.com/jump.php?AID=2917&src=home](http://www.icewalkers.com/jump.php?AID=2917&src=home).
Choice (2).
0. Save the image in the Clonezilla server.
1. Prepare a partition table (manually created by fdisk in the target machine, then use "sfdisk -d /dev/hda > pt.sf", or you can manually edit that file if you are familiar with that), and backup /home/partimag/$IMA_NAME/pt.sf, then overwrite the /home/partimag/$IMA_NAME/pt.sf.
2. Now use dcs -> clonezilla-start -> clonezilla-restore-disk in server, remember to choose option -r (Resize the partition when restoration finishes).
3. boot the client,
Choice (3).
0. Save the image in the Clonezilla server.
1. Boot the target machine as remote-linux-txt (dcs -> remote-linux-txt).
2. Login in as root in the target machine, use fdisk to create the partitions you want. Remember every partition size should be larger than that in the image file.
3. Now use dcs -> clonezilla-start -> clonezilla-restore-disk in server, remember to choose option -k (Do NOT create partition in target harddisk in client), and option -r (Resize the partition when restoration finishes).
4. boot the client,
That's all. The above scenario I am assuming you are cloning M$ windows (ntfs or fat) or Linux ext2/ext3, since that resize action need ntfsresize (already in /opt/drbl/sbin/), parted and resize2fs. These programs are already in DRBL environment. For other file systems, such as reiserfs, xfs or jfs, you have to install those resize programs in the server, and maybe manually resize is necessary after clone.


---

### Post by Fire_Chief on 2009-02-26
You can use the GParted LiveCD to do a direct copy of the partitions from the old disk to the new and resize on the fly. Then just install and configure GRUB on the new drive MBR. Boot. Success!

Cheers!

---

### Post by RedSingularity on 2009-02-26
Thats what i needed.  Thanks!

---

### Post by makisupa123 on 2009-02-26
Like Fire_chief said, gparted can do this.  Once you've copied your partitions over you can use this guide to reinstall grub on the MBR of your new disk.

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

--Mak

---

