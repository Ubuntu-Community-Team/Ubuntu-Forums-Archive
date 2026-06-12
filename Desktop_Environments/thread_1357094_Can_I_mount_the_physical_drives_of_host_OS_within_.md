---
title: "Can I mount the physical drives of host OS within a guest OS? How?"
date: 2009-12-16
forum: Desktop Environments
---

### Post by zoomiest on 2009-12-16
PROBLEM:
I have a CentOS box that suffered some non-graceful shutdowns (power interruptions). Now it won't connect to a network. So I am trying to copy off the data...

ATTEMPTED RESOLUTION:
I mounted that drive as a slave in my Ubuntu 9.10 box to copy off the data, but it won't read the data partition (LVM2), but only the /boot partition (ext3) of the CentOS slave drive.

ANOTHER ATTEMPTED RESOLUTION:
I loaded CentOS 5 as a guest OS in a VirutalBox VM, hoping I could mount the physical drives (especially one slave drive) of the Host (Ubuntu 9.10) to the guest OS (CentOS 5 running on VirtualBox), so I can then copy the data off...

But I am not seeing any way, now, to see those host-os-drives... let alone mount them.

Any help would be appreciated...

---

### Post by uniden9 on 2009-12-16
Well with I'd start by make sure lvm2 is installed on your ubuntu 9.10

sudo dpkg --list |grep lvm2
ii  lvm2                                       2.02.39-0ubuntu11                          The Linux Logical Volume Manage

If it comes back with the leading ii, its install. rc or nothing returned, you need to install it. If its not, I'd recommend install and reboot.  Gnome automounter will probably take care of your problems.
$sudo apt-get install lvm2

Scan physical volume
$sudo pvscan
  PV /dev/sdg1   VG vgfstore2   lvm2 [6.82 TB / 645.61 GB free]
Scan volume group
$sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "vgfstore2" using metadata type lvm2
Scan logical volumes
$sudo lvscan
  ACTIVE            '/dev/vgfstore2/lvfstore2_a' [6.17 TB] 

If lvscan show Inactive, you will have to activate the logical volumes for the volume group.
$sudo vgchange vgfstore2 -a y
To make sure the device mapper is populated and uuid if you use them, hit udev in the head.
$sudo restart udev
If they show up as active, all is well for lvm2

Automounter service will probably see it and auto mount the partitions at this point. To see: 
$sudo mount
It normally uses /media

If not.
mkdir /mnt/mymount
mount -t ext3 /dev/vgfstore2/lvfstore2_a /mnt/mymount -o rw

---

### Post by zoomiest on 2009-12-17
Thanks so much.
I get:

```
allan@family-ubuntu-desktop:~$ sudo dpkg --list |grep lvm2
[sudo] password for allan: 
ii  lvm2  2.02.39-0ubuntu11   The Linux Logical Volume Manager

allan@family-ubuntu-desktop:~$ sudo pvscan
  Couldn't find device with uuid 'HTFX9Q-pAsr-JP8s-maLb-6sRm-0Ipw-49uygu'.
  Couldn't find device with uuid 'jz50JU-3Vf4-blBE-J4Yd-hKQV-Z0p9-QtDyQV'.
  Couldn't find device with uuid 'HTFX9Q-pAsr-JP8s-maLb-6sRm-0Ipw-49uygu'.
  Couldn't find device with uuid 'jz50JU-3Vf4-blBE-J4Yd-hKQV-Z0p9-QtDyQV'.
  PV /dev/sdb2        VG VolGroup01   lvm2 [74.41 GB / 0    free]
  PV unknown device   VG VolGroup01   lvm2 [74.00 GB / 74.00 GB free]
  PV unknown device   VG VolGroup01   lvm2 [512.00 MB / 512.00 MB free]
  Total: 3 [148.91 GB] / in use: 3 [148.91 GB] / in no VG: 0 [0   ]
```

The /dev/sdb2 is the volume I would like to read...

But when I go further, I start to fall off...
```
allan@family-ubuntu-desktop:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Couldn't find device with uuid 'HTFX9Q-pAsr-JP8s-maLb-6sRm-0Ipw-49uygu'.
  Couldn't find all physical volumes for volume group VolGroup01.
  Couldn't find device with uuid 'HTFX9Q-pAsr-JP8s-maLb-6sRm-0Ipw-49uygu'.
  Couldn't find all physical volumes for volume group VolGroup01.
  Volume group "VolGroup01" not found

allan@family-ubuntu-desktop:~$ sudo lvscan
  Couldn't find device with uuid 'HTFX9Q-pAsr-JP8s-maLb-6sRm-0Ipw-49uygu'.
  Couldn't find all physical volumes for volume group VolGroup01.
  Couldn't find device with uuid 'HTFX9Q-pAsr-JP8s-maLb-6sRm-0Ipw-49uygu'.
  Couldn't find all physical volumes for volume group VolGroup01.
  Volume group "VolGroup01" not found
```

Can I create a new volume group without blowing away my disks? What would you suggest are next steps?

---

### Post by uniden9 on 2009-12-17
Well you have a serious problem.  It appears VolGroup01 is made up of two or three drives/partitions ( physical volumes ).  It can find one of the physical volumes on the /dev/sdb2 . From that lvm metadata it also seems to expects two more with uuid
HTFX9Q-pAsr-JP8s-maLb-6sRm-0Ipw-49uygu
jz50JU-3Vf4-blBE-J4Yd-hKQV-Z0p9-QtDyQV

Are you sure you haven't lost a drive?

To cross reference uuid's to devices Look at the symbolic links:
$ls -l /dev/disk/by-uuid
OR
sudo blkid

$sudo pvdisplay
This might give a little more on what drives its expecting. in that volume group. 

One other highly unlikely thing, lvm only scans certain drive types, sd? hd? md?, configured in /etc/lvm/lvm.conf.  It did not use to scan mapper devices, so if you had a luks crypto mapper and then lvm inside that, it would not see it.  I doubt this is true for you, since it found a drive in the pv.

---

### Post by zoomiest on 2009-12-17
... yikes... 

Do you think the resolution would be achieved faster if I just mounded this drive back in its original box, and work on the network connectivity issues? (got unceremoniously or graciously powered down, and now won't connect to the network).

It will boot up.

---

