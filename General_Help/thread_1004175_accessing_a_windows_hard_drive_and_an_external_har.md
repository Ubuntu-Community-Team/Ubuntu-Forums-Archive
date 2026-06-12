---
title: "accessing a windows hard drive and an external hard drive from ubuntu bootdisk"
date: 2008-12-06
forum: General Help
---

### Post by danielholmes85 on 2008-12-06
Hi All,

ive done something terrible to my windows installation and i cant boot windows up any more, so am trying to run ubuntu off a CD to copy across my files to an external hdd then format my pc.

Im able to boot up ubuntu 7.04 from my CD Drive but once in I can't find how to access my hard drives or the external drive. I've used linux in bits and pieces in the past, but have never really had the need to use mount and dont understand it fully anyway.

Under computer in the file browser there are:
[LIST]
[*]floppy drive
[*]cd-rom/dvd-rom drive
[*]cd-rw/DVD+rw drive
[*]39.1 GB Volume
[*]Filesystem
[/LIST]

39.1 GB was my C Drive in windows and i had a 165GB D drive which doesn't appear to be in that list and neither that disk or the external hdd seem to be mounting automatically. Trying to access the 39.1 GB drive i get the following:
```
Cannot mount volume
mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or other error. In some cases useful info is found in syslog - try dmesg | tail or so
```

Running sudo fdisk -l shows the presence of my 400 GB HDD and the 165 GB D Drive. The entry for the 165GB drive says (I can write out the full output if required):

```
Disk /dev/sdb: 164.6 GB, 16469555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table
```

If anyone can provide some help on how to access these drives it would be greatly appreciated. Thanks,

Daniel

---

### Post by jbrown96 on 2008-12-07
Is the external new? You will need to create a partition on it. There is a partition editor in System-->admin-->parition editor. Create a partition (if you are going to use it in Windows, I recommend NTFS). check your partitions with fdisk afterwards (it seems you know how to do this).

1) create mount directories
```
mkdir ./Windows && mkdir ./backup
```
2) mount drives
```
sudo mount -t auto /dev/WINDOWS_DRIVE ./Windows -o force && sudo mount -t auto /dev/EXTERNAL_DRIVE ./backup
``` Change WINDOWS_DRIVE and EXTERNAL_DRIVE to whatever you found from fdisk. 
3) copy files. You should now be able to transfer files from ./Windows to ./backup. If you get permission errors, you can chown the directories with ```
sudo chown -R ubuntu:ubuntu ./Windows ./backup
```

---

### Post by danielholmes85 on 2008-12-07
Thanks kindly for your response!

For the external drive, it worked after restarting and is always showing up now so no error there.

> 2) mount drives

tried this but got the following error: 
```
mount: unknown filesystem type 'nvidia_raid_member'
```
This reminded me of something significant which i probably should have mentioned before; that i have 2 hard drives (approx 110GB each) in raid 0 and partitioned in to 40GB and 165GB. I used nvidia drivers for the raid config (the raid setup was a silly move - i did it on recommendation from a friend and it was a little beyond my experience).

It may be of interest to note that the "Windows Recovery Console" doesn't detect my hard drives or the windows installation on them.

With the extra things i've found out, i feel the full contents of fdisk is probably relevant:

```
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x587c of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 164.6GB, 164696555520 bytes
255 heads, 63 sectors/track, 29923 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device     Boot   Start     End      Blocks  Id  System
/dev/sda1     *       1    5099    40957686   7  HPFS/NTFS
/dev/sda2          5100   40045   280703745   f  W95 Ext'd (LBA)
/dev/sda5     ?  264324  264300  2147296183  1b  Hidden W95 FAT32

Disk /dev/sda: 164.6GB, 164696555520 bytes
255 heads, 63 sectors/track, 29923 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 400.0GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device     Boot   Start     End      Blocks  Id  System
/dev/sdc1     *       1   48641   390708801   7  HPFS/NTFS
```

To me its now looking like there are some issues with the physical hard drives that may mean my trying a fix through ubuntu is futile, so if this is the case please let me know and i'll start looking elsewhere. Thanks!

---

