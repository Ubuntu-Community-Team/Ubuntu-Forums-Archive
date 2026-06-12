---
title: "GRUB map command (booting Win 7)"
date: 2009-05-20
forum: General Help
---

### Post by CANDYBOi on 2009-05-20
I'm having trouble booting into a Win 7 install (which was present before Linux on this machine).

**fdisk -lu** *(all but my W7 disk omitted - Linux resides on /dev/sdd)*:
```
Disk /dev/sde: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38c33aec

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   160083967    80040960    7  HPFS/NTFS
```


It's my understanding that Windows tends to assume it's installed on the first disk, so I thought I'd use GRUB's map command, adding this entry to /boot/grub/menu.lst
```
title       Windows 7 (RC1)
rootnoverify (hd4,0)
map (hd0) (hd4)
map (hd4 (hd0)
makeactive
chainloader +1
```

No go; it reboots. Can anyone shed any light on the situation? I feel like I've missed something rather basic somewhere.

/CANDYBOi

---

### Post by mcduck on 2009-05-20
> **CANDYBOi said:**
> I'm having trouble booting into a Win 7 install (which was present before Linux on this machine).

**fdisk -lu** *(all but my W7 disk omitted - Linux resides on /dev/sdc)*:
```
Disk /dev/sde: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38c33aec

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   160083967    80040960    7  HPFS/NTFS
```


It's my understanding that Windows tends to assume it's installed on the first disk, so I thought I'd use GRUB's map command, adding this entry to /boot/grub/menu.lst
```
title       Windows 7 (RC1)
rootnoverify (hd4,0)
map (hd0) (hd4)
map (hd4 (hd0)
makeactive
chainloader +1
```

No go; it reboots. Can anyone shed any light on the situation? I feel like I've missed something rather basic somewhere.

/CANDYBOi
If I understood correctly, you have Windows on hd4,0 and you want Windows to think that it's on the first drive (hd0,0)?

```
title       Windows 7 (RC1)
rootnoverify (hd0,0)
map (hd0) (hd4)
map (hd4) (hd0)
makeactive
chainloader +1
```

---

### Post by CANDYBOi on 2009-05-20
> **mcduck said:**
> If I understood correctly, you have Windows on hd4,0 and you want Windows to think that it's on the first drive (hd0,0)?

```
title       Windows 7 (RC1)
rootnoverify (hd0,0)
map (hd0) (hd4)
map (hd4) (hd0)
makeactive
chainloader +1
```

Exactly. I didn't realize you had to set root to 0,0 as well. I just thought GRUB used that to find the OS files, while map fooled the OS being loaded. I'll give it a shot as soon as I get home, thanks!

**EDIT:**
menu.lst entry now looks like this
```
title       Windows 7 (Loader)
rootnoverify (hd4,0)
map (hd0) (hd4)
map (hd4) (hd0)
makeactive
chainloader +1
```

I'm now getting the classic BOOTMGR error instead. Boot info script yields
```
=> Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sde and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
```
The sdd part is correct, of course. The sde part however, is not. I'd prefer if there was a way to solve this without having to reinstall GRUB at the end (if at all possible).


Here's the boot info in its entirety

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sde and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x78706abc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   490,223,474   490,223,412   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf49e7f6b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5fe15fe1

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5b6f5b6

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    76,903,154    76,903,092  83 Linux
/dev/sdd2          76,903,155    80,292,869     3,389,715   5 Extended
/dev/sdd5          76,903,218    80,292,869     3,389,652  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38c33aec

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048   160,083,967   160,081,920   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="A2C0D1FBC0D1D59F" LABEL="Maxtor" TYPE="ntfs" 
/dev/sdb1: UUID="2CBC41B6BC417AFA" LABEL="Hitachi" TYPE="ntfs" 
/dev/sdc1: UUID="587A56027A55DCF6" LABEL="Samsung" TYPE="ntfs" 
/dev/sdd1: UUID="89942d90-4ab8-451c-a86c-4b8a390dadbc" TYPE="ext3" 
/dev/sdd5: UUID="9dfe5fca-e827-4c1a-a925-37ea18c6137c" TYPE="swap" 
/dev/sde1: UUID="B8E037D0E037939A" LABEL="Se7en" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdd1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc1 on /media/Samsung type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/Hitachi type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/Maxtor type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1 on /media/Se7en type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


=========================== sdd1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=89942d90-4ab8-451c-a86c-4b8a390dadbc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=89942d90-4ab8-451c-a86c-4b8a390dadbc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		CrunchBang 8.10.02, kernel 2.6.27-9-generic
uuid		89942d90-4ab8-451c-a86c-4b8a390dadbc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=89942d90-4ab8-451c-a86c-4b8a390dadbc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		CrunchBang 8.10.02, kernel 2.6.27-9-generic (recovery mode)
uuid		89942d90-4ab8-451c-a86c-4b8a390dadbc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=89942d90-4ab8-451c-a86c-4b8a390dadbc ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		CrunchBang 8.10.02, memtest86+
uuid		89942d90-4ab8-451c-a86c-4b8a390dadbc
kernel		/boot/memtest86+.bin
quiet
##
title       Windows 7 (Loader)
rootnoverify (hd4,0)
map (hd0) (hd4)
map (hd4) (hd0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=89942d90-4ab8-451c-a86c-4b8a390dadbc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9dfe5fca-e827-4c1a-a925-37ea18c6137c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
#SAMSUNG 500GB
/dev/sdc1   /media/Samsung  ntfs    user,exec,rw    0   0
#HITACHI 232.88 GB
/dev/sdb1   /media/Hitachi  ntfs    user,exec,rw    0   0
#MAXTOR 233.76 GB
/dev/sda1   /media/Maxtor   ntfs    user,exec,rw    0   0
#Se7en 80 GB
/dev/sde1   /media/Se7en    ntfs    user,exec,rww   0   0        

=================== sdd1: Location of files loaded by Grub: ===================


  13.4GB: boot/grub/menu.lst
  13.4GB: boot/grub/stage2
  13.4GB: boot/initrd.img-2.6.27-9-generic
  13.4GB: boot/vmlinuz-2.6.27-9-generic
  13.4GB: initrd.img
  13.4GB: vmlinuz
```

---

### Post by CANDYBOi on 2009-05-20
I just realized something else that's kind of weird (to me).
I got it wrong; booting **hd4** actually gives the NTLDR error (an old XP install..?), while **hd3** gives the BOOTMGR. What gives?

I'm including devices.map as well
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde
```

/CANDYBOi

---

### Post by mcduck on 2009-05-20
Grub device numbering doesn't always directly correspond with the device naming used by Linux itself, you should probably use "sudo fdisk -l" to check the partition order it reports. I can't really help with finding out the correct partition for Grub without full fdisk output.

Anyway, the thing with grub mapping is that you want to make the partition in question seem like the first partition, and then boot the (now) first partition.

This would make the first partition seem like fifth one, and fourth partition seem like first one. And then it boots the fifth partition (the one that's fifth partition *after* remapping the partitions). In other words you make the first partition seem like it's the fifth one, and then boot that. The result is the same you would get by no drive mapping at all and just booting from hd0,0.
```

title       Windows 7 (RC1)
rootnoverify (hd4,0)
map (hd0) (hd4)
map (hd4) (hd0)
makeactive
chainloader +1
```
-hd0 becomes hd4
-hd4 becomes hd0
-boot from hd4 (really hd0)

To make the fifth partition seem like first one, and then boot from that partition, you need to map that partition to first one, and then boot from what *now* is the first partition:
```

title       Windows 7 (RC1)
rootnoverify (hd0,0)
map (hd0) (hd4)
map (hd4) (hd0)
makeactive
chainloader +1
```
- hd0 becomes hd4
- hd4 becomes hd0
- boot from hd0 (really hd4)

---

### Post by CANDYBOi on 2009-05-20
Sorry, forgot to mention it in the last post. I did try rootnoverify (hd0,0) as well, resulting in Error 13 (Inval or unsupp exec format).

**fdisk -l**
```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78706abc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30515   245111706    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf49e7f6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fe15fe1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5b6f5b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        4787    38451546   83  Linux
/dev/sdd2            4788        4998     1694857+   5  Extended
/dev/sdd5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sde: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38c33aec

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        9965    80040960    7  HPFS/NTFS

```

---

