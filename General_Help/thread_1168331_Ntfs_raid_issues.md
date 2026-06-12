---
title: "Ntfs raid issues"
date: 2009-05-24
forum: General Help
---

### Post by tmackay on 2009-05-24
recently i got myself a new video card...

unfortunately my power supply could only handle it and my one of  my two (not redundant) raid 0 stripe arrays

Unfortunately i didn't figure that out until both the ntfs.sys files corrupted.
windows bsod (stop 0...012)

I killed off the windows partition with a low-format and reinstalled. My data drive i simply left semi intact and unplugged until i found a spare power supply.

now with a few spare  10G drives one fat32 adn one where i installed Ubuntu 9.04
I am attempting to recoop the "abyss"

I followed a few other threads but i have something happening that seems to be derailing my progress
```

mackat@mackat-desktop:~$ sudo dmraid -tay
[sudo] password for mackat: 
isw_cfifgahcjh_RAID: 0 72303360 linear /dev/sdc 0
sil_agagdddebbdf: 0 1953575936 striped 4 128 /dev/sde 0 /dev/sdf 0 /dev/sdg 0 /dev/sdh 0

mackat@mackat-desktop:~$ sudo dmraid -ay
RAID set "isw_cfifgahcjh_RAID" was activated
RAID set "sil_agagdddebbdf" already active
ERROR: dos: partition address past end of RAID device

mackat@mackat-desktop:~$ sudo mount -t ntfs /dev/mapper/sil_agagdddebbdf /winraid
NTFS signature is missing.
Failed to mount '/dev/mapper/sil_agagdddebbdf': Invalid argument
The device '/dev/mapper/sil_agagdddebbdf' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

mackat@mackat-desktop:~$ sudo fdisk -l

Disk /dev/sda: 10.2 GB, 10254827520 bytes
16 heads, 63 sectors/track, 19870 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xdc39f7d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       19869    10013944+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe37da55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1188     9542578+  83  Linux
/dev/sdb2            1189        1247      473917+   5  Extended
/dev/sdb5            1189        1247      473886   82  Linux swap / Solaris

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dff2dfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9000    72292468+   7  HPFS/NTFS

Disk /dev/sdd: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95a710b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121604   976784098+   7  HPFS/NTFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/sdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdg doesn't contain a valid partition table

Disk /dev/sdh: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdh doesn't contain a valid partition table

mackat@mackat-desktop:~$ sudo dmraid -r
/dev/sdh: sil, "sil_agagdddebbdf", stripe, ok, 488393984 sectors, data@ 0
/dev/sdg: sil, "sil_agagdddebbdf", stripe, ok, 488393984 sectors, data@ 0
/dev/sdf: sil, "sil_agagdddebbdf", stripe, ok, 488393984 sectors, data@ 0
/dev/sde: sil, "sil_agagdddebbdf", stripe, ok, 488393984 sectors, data@ 0
/dev/sdc: isw, "isw_cfifgahcjh", GROUP, ok, 72303838 sectors, data@ 0
```


I also noticed variations on the way dmraid activated the sil3114 set sometimes it creates 2 sets of raid 0 instead of a full  raid 0 set

I have been unable to divine the proper syntax to manually configure the sets from the man pages and the forums

---

### Post by ronparent on 2009-05-24
This is a head spinner alright! What appears in /dev/mapper? This could be the key to identifying symbolic links for individual partitions and mounting them.

---

### Post by tmackay on 2009-05-25
after a reboot here we are:
```

mackat@mackat-desktop:/dev/mapper$ ls
control  sil_agagdddebbdf  sil_agagdddebbdf1

mackat@mackat-desktop:/dev/mapper$ sudo dmraid -ay
[sudo] password for mackat: 
RAID set "isw_cfifgahcjh_RAID" was activated
RAID set "sil_agagdddebbdf" already active
ERROR: dos: partition address past end of RAID device

mackat@mackat-desktop:/dev/mapper$ ls
control  isw_cfifgahcjh_RAID  sil_agagdddebbdf  sil_agagdddebbdf1

mackat@mackat-desktop:/dev/mapper$ sudo mount -t ntfs /dev/mapper/isw_cfifgahcjh_RAID /winraid
NTFS signature is missing.
Failed to mount '/dev/mapper/isw_cfifgahcjh_RAID': Invalid argument
The device '/dev/mapper/isw_cfifgahcjh_RAID' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

mackat@mackat-desktop:/dev/mapper$ sudo mount -t ntfs /dev/mapper/sil_agagdddebbdf /winraid
NTFS signature is missing.
Failed to mount '/dev/mapper/sil_agagdddebbdf': Invalid argument
The device '/dev/mapper/sil_agagdddebbdf' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

mackat@mackat-desktop:/dev/mapper$ sudo mount -t ntfs /dev/mapper/sil_agagdddebbdf1 /winraid
The disk contains an unclean file system (0, 1).
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

the last one looked promising but windows can't cope to run chkdsk

and i'm not sure what the second path is telling me to do.

---

### Post by ronparent on 2009-05-25
Your output of dmraid -ay is troubling. Any existing partitions on the array should be made active also. 

ie 
ron-2@ron-LR-desktop:~$ sudo dmraid -ay
/dev/sdb: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sda: "sil" and "nvidia" formats discovered (using nvidia)!
RAID set "nvidia_aebhdfib" was activated
RAID set "nvidia_aebhdfib1" was activated
RAID set "nvidia_aebhdfib5" was activated
RAID set "nvidia_aebhdfib6" was activated
RAID set "nvidia_aebhdfib7" was activated
RAID set "nvidia_aebhdfib8" was activated
RAID set "nvidia_aebhdfib9" was activated
RAID set "nvidia_aebhdfib10" was activated
RAID set "nvidia_aebhdfib11" was activated
RAID set "nvidia_aebhdfib12" was activated

I don't know what to tell you from here. If the partitions in the raid cannot be recognized by windows (and assigned a drive letter) on boot, they may well not be recoverable.

---

### Post by tmackay on 2009-05-26
any body have any insight why the working ntfs raid partition isn't mountable?

(isw_cfifgahcjh_RAID)

when i get home i'm going to try running chkdsk /f on the working raid set to see if that makes it mountable.

---

### Post by ronparent on 2009-05-26
The isw_cfifgahcjh_RAID reference is not a partition, it is the entire drive/array. The same reference followed by a number (ie 1, 2, etc) would be your valid partitions which would be mountable.

---

