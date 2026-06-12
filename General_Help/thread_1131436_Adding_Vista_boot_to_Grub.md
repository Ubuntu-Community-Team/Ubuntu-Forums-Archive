---
title: "Adding Vista boot to Grub"
date: 2009-04-20
forum: General Help
---

### Post by NuBiXx on 2009-04-20
I have Vista installed on my hard drive then I bought another hard drive and installed Ubuntu on the second hard drive separately.
.

So it's like this,
Hard drive 1 installed Vista on it then I physically disconnected the hard drive 1 and then installed hard drive 2 then installed Ubuntu on that so I would like to edit Grub to add Vista's boot info can someone please tell me how? thanks

lshw -businfo -C disk

Bus info          Device      Class       Description
=====================================================
scsi@0:0.1.0      /dev/sda    disk        120GB WDC WD1200BB-00R
scsi@2:0.0.0      /dev/sdb    disk        320GB Hitachi HDP72503
scsi@4:0.0.0      /dev/cdrom  disk        DVD A  DH16A6L-C
scsi@7:0.0.0      /dev/sdc    disk        SCSI Disk
scsi@7:0.0.1      /dev/sdd    disk        SCSI Disk
scsi@7:0.0.2      /dev/sde    disk        SCSI Disk
scsi@7:0.0.3      /dev/sdf    disk        SCSI Disk
scsi@6:0.0.0      /dev/sdg    disk        Stylus Storage
                  /dev/sdg    disk        


Vista is installed on the 320GB Hitachi

---

### Post by DGortze380 on 2009-04-20
> **NuBiXx said:**
> I have Vista installed on my hard drive then I bought another hard drive and installed Ubuntu on the second hard drive separately.
.

So it's like this,
Hard drive 1 installed Vista on it then I physically disconnected the hard drive 1 and then installed hard drive 2 then installed Ubuntu on that so I would like to edit Grub to add Vista's boot info can someone please tell me how? thanks

lshw -businfo -C disk

Bus info          Device      Class       Description
=====================================================
scsi@0:0.1.0      /dev/sda    disk        120GB WDC WD1200BB-00R
scsi@2:0.0.0      /dev/sdb    disk        320GB Hitachi HDP72503
scsi@4:0.0.0      /dev/cdrom  disk        DVD A  DH16A6L-C
scsi@7:0.0.0      /dev/sdc    disk        SCSI Disk
scsi@7:0.0.1      /dev/sdd    disk        SCSI Disk
scsi@7:0.0.2      /dev/sde    disk        SCSI Disk
scsi@7:0.0.3      /dev/sdf    disk        SCSI Disk
scsi@6:0.0.0      /dev/sdg    disk        Stylus Storage
                  /dev/sdg    disk        


Vista is installed on the 320GB Hitachi

please post the output of 
fdisk -l

GRUB should have updated during the install if both drives were connected

---

### Post by raedbenz on 2009-04-21
try download and install **GParted** on ubuntu.
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

---

