---
title: "Grub hangs freezes at &quot;starting up...&quot; fix"
date: 2009-01-11
forum: General Help
---

### Post by csumm101 on 2009-01-11
After reinstalling ubuntu 8.04 on different drive i found that ubuntu would boot without problem but winxp wouldn't boot. It always froze at at the phrase, "starting up...". It didn't matter how long you waited, it wouldn't change.
ubuntu was installed on hard drive hd1
windows was installed on hard drive hd0

I had to edit the file: /boot/grub/menu.lst


What used to say:
title Microsoft Windows XP Professional
root (hd1,0)
chainloader +1
savedefault


I edited it to say:
title Microsoft Windows XP Professional
root (hd1,0)
chainloader +1
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)

Now I can boot into windows xp - no prob

---

### Post by Stretsh on 2009-01-11
> **csumm101 said:**
> ubuntu was installed on hard drive hd1
**windows was installed on hard drive hd0**

...

[B]title Microsoft Windows XP Professional
root (hd1,0)[/B]

Thanks a million man! Funny thing that about half an hour before I got this problem, you post the solution!

Small correction: in the first mention you switched hd1 and hd0. According to your menu.lst the XP drive is hd1, and ubuntu is hd0.

---

### Post by BLTicklemonster on 2009-01-23
I have an interesting situation. I installed Windows 7 on a hard drive all by itself just to keep from messing up my ubuntu boot ability, yes, windows installed after ubuntu, but by itself, no other drives attached. I then noticed that people were dual booting, and saw where you could get a dual boot even if you installed windows after ubuntu was installed.

I tried last night and never got that to work...

So, my problem is simple:

At present, the hd with windows is the master in the sole ide slot on my motherboard. The dvd/rw is slaved to it. I have a maxtor ultra ata 133 controller in a pci slot that has both ide slots used, the first one has a master and a slave, the master containing one of my ubuntu installs, and the slave is just partitioned for storage. The second ide slot has a hard drive on it that is partitioned, but also has an ubuntu installed on it, on the second partition.

here's grub finding my stage1 s:

```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,2)
 (hd2,0)
grub> 
```

Good so far, 0,2 is the newest install (specifically so I might get windows 7 to show up), and it's on the first ide slot of the maxtor ultra ata 133 controller, 2,0 is the drive on the second ide slot on the controller. Which makes no sense to me, but that's beside the point. BECAUSE windows is the first drive by my reckoning, because it's sitting on a cable that's plugged directly into the board ergo hd0,* by my reckoning. But that ain't how it works, right?

THEREFORE, how do I determine if the windows os is on which (hd*,*)? I know the drive has two partitions, and suspect that the os is on the second partition, but how do I edit grub to load it? By the way, I did a fresh install of ubuntu after setting the drives up the way they are now, and windows didn't show up in menu.lst at all.

So, there's 4 drives, we already know 0 and 2 have ubuntu on them, which leaves, what, 1 and 3, right? 0,1,2,3, yeah, that's 4, okay. So do I just start whamming away at menu.lst adding 

```
 Title		Windows 7
root		(hd1,)
makeactive
chainloader	+1
```

Nope, I get:
Error 21: Selected disk does not exist.

then maybe

```
Title		Windows 7
root		(hd3,1)
makeactive
chainloader	+1
```
Nope, I get:
Error 12: Invalid Device Required.

AHA, something is there! But what? Maybe windows, but it doesn't want to load? So I try this:

```
Title		Other operating systems: WINDOWS 7 ULTIMATE BETA
root		(hd1,1)
chainloader	+1
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
```
And still get the Error 12.

So, the question is, where is Windows? I installed Ubuntu with Windows present, so I reckoned that, as in the old days, it would show up or the drive would be present and mountable, but it's not.

fdisk -l
```
Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01260126

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            4666        4870     1646662+   5  Extended
/dev/sda3   *           1        4665    37471581   83  Linux
/dev/sda5            4666        4870     1646631   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10791078

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   b  W95 FAT32
/dev/sdb2            3825       10011    49697077+   f  W95 Ext'd (LBA)
/dev/sdb5            3825        6374    20482843+   b  W95 FAT32
/dev/sdb6            6375        6526     1220908+  82  Linux swap / Solaris
/dev/sdb7            6527       10011    27993231    b  W95 FAT32

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38903890

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3824    30716248+  83  Linux
/dev/sdc4            3825       19457   125572072+   5  Extended
/dev/sdc5            3825       10883    56701386    b  W95 FAT32
/dev/sdc6           10884       19102    66019086    b  W95 FAT32
/dev/sdc7           19103       19457     2851506   82  Linux swap / Solaris

```

There theres the results of running 
```
sudo bash ~/Desktop/boot_info_script*.sh
```
from here: [https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/) thanks to caljohnsmith and I get all of this:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc4: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01260126

Partition  Boot        Start          End         Size  Id System

/dev/sda2         74,943,225   78,236,549    3,293,325   5 Extended
/dev/sda5         74,943,288   78,236,549    3,293,262  82 Linux swap / Solaris
/dev/sda3    *            63   74,943,224   74,943,162  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10791078

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *            63   61,432,559   61,432,497   b W95 FAT32
/dev/sdb2         61,432,560  160,826,714   99,394,155   f W95 Ext'd (LBA)
/dev/sdb5         61,432,623  102,398,309   40,965,687   b W95 FAT32
/dev/sdb6        102,398,373  104,840,189    2,441,817  82 Linux swap / Solaris
/dev/sdb7        104,840,253  160,826,714   55,986,462   b W95 FAT32


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38903890

Partition  Boot        Start          End         Size  Id System

/dev/sdc1    *            63   61,432,559   61,432,497  83 Linux
/dev/sdc4         61,432,560  312,576,704  251,144,145   5 Extended
/dev/sdc5         61,432,623  174,835,394  113,402,772   b W95 FAT32
/dev/sdc6        174,835,458  306,873,629  132,038,172   b W95 FAT32
/dev/sdc7        306,873,693  312,576,704    5,703,012  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda3: UUID="52dc37dc-37a8-45c2-b800-f1e042226dbc" TYPE="reiserfs" 
/dev/sda5: UUID="6e4d7df9-832e-4e2a-91f2-2a622b47ab44" TYPE="swap" 
/dev/sdb1: UUID="47DC-81D8" TYPE="vfat" 
/dev/sdb5: LABEL="STORAGE" UUID="5CE6-F939" TYPE="vfat" 
/dev/sdb6: UUID="49d2c741-9972-42f3-b11c-c6f1ca98c176" TYPE="swap" 
/dev/sdb7: UUID="474E-44A3" TYPE="vfat" 
/dev/sdc1: UUID="31232a92-82fd-41a5-92da-2d867c1ca723" TYPE="reiserfs" 
/dev/sdc5: LABEL="MOVIES" UUID="4737-7180" TYPE="vfat" 
/dev/sdc6: UUID="488A-9939" TYPE="vfat" 
/dev/sdc7: TYPE="swap" UUID="a6df1aa7-9cb7-49a2-a249-fe1ae870648b" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type reiserfs (rw,relatime,notail)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/bill/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bill)
/dev/sdb5 on /media/STORAGE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb7 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb1 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda3 on /media/disk-2 type reiserfs (rw,nosuid,nodev,uhelper=hal)
/dev/sdc5 on /media/Movies type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc6 on /media/disk-3 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

=========================== sda3/boot/grub/menu.lst: ===========================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Windows 7 Ultimate Beta


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-23-rt (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-23-rt (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-23-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-22-rt (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-22-rt (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-22-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-21-rt (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-21-rt (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-21-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-19-rt (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-19-rt (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc /               reiserfs notail,relatime 0       1
# /dev/sda5
UUID=6e4d7df9-832e-4e2a-91f2-2a622b47ab44 none            swap    sw              0       0
# /dev/sdb6
UUID=49d2c741-9972-42f3-b11c-c6f1ca98c176 none            swap    sw              0       0
# /dev/sdc7
UUID=a6df1aa7-9cb7-49a2-a249-fe1ae870648b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location  of files loaded by Grub: ===================


  10.4GB: boot/grub/menu.lst
  10.4GB: boot/grub/stage2
  10.4GB: boot/initrd.img-2.6.24-16-generic
    .1GB: boot/initrd.img-2.6.24-16-generic.bak
  10.5GB: boot/initrd.img-2.6.24-23-generic
  10.5GB: boot/initrd.img-2.6.24-23-generic.bak
    .1GB: boot/vmlinuz-2.6.24-16-generic
  10.4GB: boot/vmlinuz-2.6.24-23-generic
  10.5GB: initrd.img
  10.4GB: initrd.img.old
  10.4GB: vmlinuz
    .1GB: vmlinuz.old

=========================== sdc1/boot/grub/menu.lst: ===========================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=31232a92-82fd-41a5-92da-2d867c1ca723 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=31232a92-82fd-41a5-92da-2d867c1ca723 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=31232a92-82fd-41a5-92da-2d867c1ca723 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=31232a92-82fd-41a5-92da-2d867c1ca723 /               reiserfs notail,relatime 0       1
# /dev/sda5
UUID=6e4d7df9-832e-4e2a-91f2-2a622b47ab44 none            swap    sw              0       0
# /dev/sdb6
UUID=49d2c741-9972-42f3-b11c-c6f1ca98c176 none            swap    sw              0       0
# /dev/sdc7
UUID=a6df1aa7-9cb7-49a2-a249-fe1ae870648b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location  of files loaded by Grub: ===================


   8.3GB: boot/grub/menu.lst
   8.3GB: boot/grub/stage2
   8.3GB: boot/initrd.img-2.6.24-16-generic
    .1GB: boot/initrd.img-2.6.24-16-generic.bak
    .1GB: boot/vmlinuz-2.6.24-16-generic
   8.3GB: initrd.img
    .1GB: vmlinuz

=============================== StdErr Messages: ===============================

No errors were reported.
```

Which may say that windows is installed in the MBR of sdc, but that's just a relic from me not reformatting a drive, as you can see if you look through all that and see sdc1, that's a storage drive, not Windows 7.

So, ah, any ideas?

---

### Post by caljohnsmith on 2009-01-24
You're booting setup is rather complicated right now, because you have Grub installed to the MBR of both your sda and sdb drives, and yet Grub in the MBR of those drives points to the 3rd boot drive for its boot files (menu.lst and stage2). So are you successfully getting the Grub menu on start up? I'm guessing you are probably booting the sda drive on start up, and if so, I would recommend reinstalling Grub to the MBR of sda so that it points to the Ubuntu installation on that drive, i.e. sda3. That way your drives won't be dependent on each other for booting. If that sounds good to you, how about doing:
```
sudo grub
grub> root (hd0,2)
grub> setup (hd0)
grub> quit
```
Then you should be able to boot into the sda3 Ubuntu install. About Windows 7 though, the script was not even able to identify your Windows 7 install on any of the partitions, so that's a bad sign. So which partition has Windows 7? Is it sdb1? Also, is there some particular reason you wanted to use FAT32 instead of NTFS for the file system? Generally NTFS is preferred. How about posting:
```
sudo mount /dev/sdb1 /mnt && ls -l /mnt
```
And we can go from there.

---

### Post by BLTicklemonster on 2009-01-24
I probably will get grub to load from sda3, as I don't care to have to scroll down to my default Ubuntu install. sdb* is all storage stuff.

Interestingly enough, the other night when I was playing around, I could open the home folder, and on the left all drives were shown, and it indeed showed both partitions on the drive that Windows is loaded on. sdc1 was small and had a few things on it, and sdc2 had the actual windows 7 installation on it.

That was when I was booting from sda3, so I'm hoping they will show back up if I use sda3 as my stage1. 

I'll be baaack.

---

### Post by BLTicklemonster on 2009-01-24
Okay, I'm booting from sda3 now. 

```
bill@bill-desktop:~$ sudo mount /dev/sdb1 /mnt && ls -l /mn
[sudo] password for bill: 
ls: cannot access /mn: No such file or directory

```

Bummer.

Here's a shot of my system monitor after I manually mount all drives:

[IMG]http://img530.imageshack.us/img530/5540/sysmonnt4.png[/IMG]

And here's the script you said to run, once again, but with the present grub settings, if there's a difference...

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc4: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01260126

Partition  Boot        Start          End         Size  Id System

/dev/sda2         74,943,225   78,236,549    3,293,325   5 Extended
/dev/sda5         74,943,288   78,236,549    3,293,262  82 Linux swap / Solaris
/dev/sda3    *            63   74,943,224   74,943,162  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10791078

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *            63   61,432,559   61,432,497   b W95 FAT32
/dev/sdb2         61,432,560  160,826,714   99,394,155   f W95 Ext'd (LBA)
/dev/sdb5         61,432,623  102,398,309   40,965,687   b W95 FAT32
/dev/sdb6        102,398,373  104,840,189    2,441,817  82 Linux swap / Solaris
/dev/sdb7        104,840,253  160,826,714   55,986,462   b W95 FAT32


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38903890

Partition  Boot        Start          End         Size  Id System

/dev/sdc1    *            63   61,432,559   61,432,497  83 Linux
/dev/sdc4         61,432,560  312,576,704  251,144,145   5 Extended
/dev/sdc5         61,432,623  174,835,394  113,402,772   b W95 FAT32
/dev/sdc6        174,835,458  306,873,629  132,038,172   b W95 FAT32
/dev/sdc7        306,873,693  312,576,704    5,703,012  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda3: UUID="52dc37dc-37a8-45c2-b800-f1e042226dbc" TYPE="reiserfs" 
/dev/sda5: UUID="6e4d7df9-832e-4e2a-91f2-2a622b47ab44" TYPE="swap" 
/dev/sdb1: UUID="47DC-81D8" TYPE="vfat" 
/dev/sdb5: LABEL="STORAGE" UUID="5CE6-F939" TYPE="vfat" 
/dev/sdb6: UUID="49d2c741-9972-42f3-b11c-c6f1ca98c176" TYPE="swap" 
/dev/sdb7: UUID="474E-44A3" TYPE="vfat" 
/dev/sdc1: UUID="31232a92-82fd-41a5-92da-2d867c1ca723" TYPE="reiserfs" 
/dev/sdc5: LABEL="MOVIES" UUID="4737-7180" TYPE="vfat" 
/dev/sdc6: UUID="488A-9939" TYPE="vfat" 
/dev/sdc7: UUID="a6df1aa7-9cb7-49a2-a249-fe1ae870648b" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda3 on / type reiserfs (rw,relatime,notail)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/bill/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bill)
/dev/sdb1 on /mnt type vfat (rw)

=========================== sda3/boot/grub/menu.lst: ===========================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Windows 7 Ultimate Beta


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-23-rt (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-23-rt (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-23-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-22-rt (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-22-rt (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-22-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-21-rt (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-21-rt (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-21-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-19-rt (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-19-rt (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=01fdbc7c-4e45-47bf-b5a2-4e817d9b7b03 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc /               reiserfs notail,relatime 0       1
# /dev/sda5
UUID=6e4d7df9-832e-4e2a-91f2-2a622b47ab44 none            swap    sw              0       0
# /dev/sdb6
UUID=49d2c741-9972-42f3-b11c-c6f1ca98c176 none            swap    sw              0       0
# /dev/sdc7
UUID=a6df1aa7-9cb7-49a2-a249-fe1ae870648b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location  of files loaded by Grub: ===================


  10.4GB: boot/grub/menu.lst
  10.4GB: boot/grub/stage2
  10.4GB: boot/initrd.img-2.6.24-16-generic
    .1GB: boot/initrd.img-2.6.24-16-generic.bak
  10.5GB: boot/initrd.img-2.6.24-23-generic
  10.5GB: boot/initrd.img-2.6.24-23-generic.bak
    .1GB: boot/vmlinuz-2.6.24-16-generic
  10.4GB: boot/vmlinuz-2.6.24-23-generic
  10.5GB: initrd.img
  10.4GB: initrd.img.old
  10.4GB: vmlinuz
    .1GB: vmlinuz.old

=========================== sdc1/boot/grub/menu.lst: ===========================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=31232a92-82fd-41a5-92da-2d867c1ca723 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=31232a92-82fd-41a5-92da-2d867c1ca723 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=31232a92-82fd-41a5-92da-2d867c1ca723 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems: WINDOWS 7 ULTIMATE BETA
root		(hd1,0)
chainloader	+1
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=52dc37dc-37a8-45c2-b800-f1e042226dbc ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=31232a92-82fd-41a5-92da-2d867c1ca723 /               reiserfs notail,relatime 0       1
# /dev/sda5
UUID=6e4d7df9-832e-4e2a-91f2-2a622b47ab44 none            swap    sw              0       0
# /dev/sdb6
UUID=49d2c741-9972-42f3-b11c-c6f1ca98c176 none            swap    sw              0       0
# /dev/sdc7
UUID=a6df1aa7-9cb7-49a2-a249-fe1ae870648b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location  of files loaded by Grub: ===================


   8.3GB: boot/grub/menu.lst
   8.3GB: boot/grub/stage2
   8.3GB: boot/initrd.img-2.6.24-16-generic
    .1GB: boot/initrd.img-2.6.24-16-generic.bak
    .1GB: boot/vmlinuz-2.6.24-16-generic
   8.3GB: initrd.img
    .1GB: vmlinuz

=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sdb7: device is busy
umount: /tmp/BootInfo/sdb7: device is busy
umount: /tmp/BootInfo/sdc5: device is busy
umount: /tmp/BootInfo/sdc5: device is busy
umount: /tmp/BootInfo/sdc6: device is busy
umount: /tmp/BootInfo/sdc6: device is busy
```

Sorry I didn't start a new thread, but I was hoping to tag along in a thread where people who were already working on this might find this and chime in if they had any help. Thanks for your help, by the way.

---

### Post by BLTicklemonster on 2009-01-24
Okay, so I've tried 

1,1 invalid device
1,0 not a bootable disk
2,1 does not exist (had to use the live cd to edit grub because this one screwed the pooch bad)
2,0 afraid to even try after the above fiasco!
3,0 does not exist
3,1 does not exist

So... grub is supposed to list according to bios. Well, windows 7 is the master on the onboard ide slot. The other drives are on my pci mount maxtor ata 133 controller. I don't see how grub is picking up sda3 as being hd0. Even if it's viewing the controller, sda3 is on the second ide slot as master. What if I moved the windows 7 drive to master on ide one on the controller, and used the onboard ide for the dvd/rw only?

Heck, why not? I feel I will have to do something about supper, the natives are revolting. (no, really they are, they all look like me!)

I'll be back later, and will have moved all my hard drives to the ata 133 controller card with just the dvd/rw on the onboard ide slot, and will let you know what I have found. Hopefully I won't be able to boot, and will have to let grub find stage1 again. That will be a good sign, I think.

---

### Post by BLTicklemonster on 2009-01-24
Solved but in a way not expected. I'm in Windows 7 now posting this.

As I was shutting down my computer to move everything around, I was wondering why the windows 7 drive never showed up, when I had a dreadful premonition. 

Sure enough, I'm beyond stupid, and yep, you just figured it out, also.

Soooo, I plugged in the stinking power coupling to the stinking hard drive and kicked myself a few times, booted, and voila.

(hd3,0) is right. The first partition has the boot manager in it, after all. (I'll have to boot back to ubuntu to be sure, of course, but it works now)

Thank you for your help, Smith, and I apologize for the drama!

Ya live ya learn, I reckon.

(kicks self again for good measure)

:p

---

### Post by caljohnsmith on 2009-01-24
That's funny, but I'm glad it actually turned out to be something simple. Cheers and enjoy Windows 7 and Ubuntu.

---

### Post by BLTicklemonster on 2009-01-24
Thanks. I'll be enjoying Ubuntu, but Windows 7 is a bit buggy, which is to be expected, I guess!

---

### Post by BLTicklemonster on 2009-01-24
Yep, Ubuntu boots, also.

Once again, thanks for your help.

---

