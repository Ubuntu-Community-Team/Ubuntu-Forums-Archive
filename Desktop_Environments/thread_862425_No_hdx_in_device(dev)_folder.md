---
title: "No hdx in device(dev) folder"
date: 2008-07-17
forum: Desktop Environments
---

### Post by NoJock on 2008-07-17
Have know idea of how to fix this some help would be appreciated.ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-07-16 11:17 4619-2E7D -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-07-16 11:17 47D9-C4D3 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-07-16 11:17 4f50d94a-9b75-46c4-9b18-b1cef1bcab5d -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-07-16 11:17 B49C5E489C5E04F0 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-07-16 11:17 bdd2459c-5c25-4ea8-bba2-5f726644c3a0 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-07-16 11:17 c796e6b0-bac0-496f-b3b5-c131467eae8e -> ../../sdb3
lrwxrwxrwx 1 root root 10 2008-07-16 11:17 cf7534f8-5a2f-4e1e-8068-6ac2cabbef06 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-07-16 11:17 d0451a7d-93c7-4674-bc7a-8bfb06c03967 -> ../../sda5
lee@lee-ult:~$ fdisk -l
lee@lee-ult:~$ sudo fdisk -l
[sudo] password for lee: 

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b7578

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3863    31029516   83  Linux
/dev/sda2            3864       10403    52532550    f  W95 Ext'd (LBA)
/dev/sda3           10404       71186   488239447+   c  W95 FAT32 (LBA)
/dev/sda4           71187       91201   160770487+   b  W95 FAT32
/dev/sda5            3864        6674    22579326   83  Linux
/dev/sda6            6675       10403    29953161   83  Linux

Disk /dev/sdb: 45.0 GB, 45020602368 bytes
255 heads, 63 sectors/track, 5473 cylinders
Units = cylinders of 16065 * 512 = 8225280 byteslee@lee-ult:~$ df -k | grep /dev
/dev/sda6             29716700   8294512  19924532  30% /
udev                   1037868        92   1037776   1% /dev
devshm                 1037868        48   1037820   1% /dev/shm
lee@lee-ult:~$ df -k | grep /dev
/dev/sda6             29716700   8294512  19924532  30% /
udev                   1037868        92   1037776   1% /dev
devshm                 1037868        48   1037820   1% /dev/shm

Disk identifier: 0x043524a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1597    12827871    7  HPFS/NTFS
/dev/sdb2            1853        5473    29085682+  83  Linux
/dev/sdb3            1598        1852     2048287+  82  Linux swap / Solaris


lee@lee-ult:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdf6
UUID=bdd2459c-5c25-4ea8-bba2-5f726644c3a0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sde3
UUID=c796e6b0-bac0-496f-b3b5-c131467eae8e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

lee@lee-ult:~$ df -k | grep /dev
/dev/sda6             29716700   8294512  19924532  30% /
udev                   1037868        92   1037776   1% /dev
devshm                 1037868        48   1037820   1% /dev/shm

lee@lee-ult:~$ df -kh
Filesystem          [SIZE="2"][FONT="Arial"][/FONT][/SIZE]  Size  Used Avail Use% Mounted on
/dev/sda6              29G  8.0G   20G  30% /
varrun               1014M  124K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   92K 1014M   1% /dev
devshm               1014M   48K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       29G  8.0G   20G  30% /home/lee/.gvfs
/dev/sda3             466G  147G  320G  32% /media/disk
/dev/sdb1              13G  7.7G  4.6G  63% /media/disk-1
/dev/sda5              22G  3.1G   18G  15% /media/disk-2
/dev/sdb2              28G  3.6G   23G  14% /media/disk-3
/dev/sda4             154G   71M  154G   1% /media/disk-4
/dev/sda1              30G  5.3G   23G  19% /media/disk-5

does not work like all the other Ubuntu i have played with.

---

### Post by mcduck on 2008-07-17
What's the problem?

If you are only worried about the hdX vs sdX thing, that's how it's supposed to be. The developers found out that the SATA/SCSI driver actually handles PATA drives better than the actual PATA driver did. So, now all hard drives are handled by the SATA/SCSI driver and thus named as sdX..

---

### Post by NoJock on 2008-07-17
Thanks that makes good sense, but know how do i fix the fstab so it mount the drive and boot and gives me something other than 13.5gb media, would like to have drives called by name or OS not (size media) any suggestions??

---

### Post by ajgreeny on 2008-07-17
You will need to add a label to the partitions, I think.  You should be able to do that with tune2fs, which is a standard ubuntu utility.  ```
man tune2fs
``` for more info.

---

### Post by NoJock on 2008-07-17
Not sure i want to learn a new way of doing things would like to just edit the fstab and be done with it, even though havent found how to do that for 8.04 it just confusing.

---

### Post by ajgreeny on 2008-07-17
I'm not 100% certain, but I don't think an edit of fstab will have any effect on the naming of the mounted devices, you will still need to label them separately in some way.  fstab just sets mount points, and I think even if you rename these as more useful names they may still be seen as generic names.  I could be wrong about this so don't take this as absolute truth, wait for other posts to confirm this, or not.

---

### Post by mcduck on 2008-07-17
You can add the drives to fstab just like it's been always done. Nothing has really changed.

But I recommend using the partition's UUID in fstab instead of the device name.

The mount point you define in fstab will be the name used for mounting your partition. Setting label won't really make any difference as the mount point defined in fstab would just override it. (but labeling partitons is of course usefull for portable drives..)

If you can tell which partition you want to add to fstab and where you want to mount it I can give you the line for your fstab, but like I said, the fstab still works just like before. The device naming change doesn't make any difference, you give fstab the name or UUID of the device you want to ount, where you want it mounted and the mount options, just like before.

---

### Post by NoJock on 2008-07-18
Thanks mcduck, i think the developers have lost there mind in a sense. Thy have broken some thing that worked. They want to change how thing work maybe it less work for them. Now you cant reference a Linux book or article on drive structure for Ubuntu now wants to be like Windows Vista and just put out a product thy like them selfs and thats it. I think this is a bug and if it the developers want to re wright the all the books published then they might as well do so. Ill stay with 7.10 for now and try the next one out and if it like the fish ( Hardy Heron ) might go some where else. Gusty Gibbon 7.10  just works and 8.04 is buggy by my standards and redevelopment does cause bug's and making all drives look like sata drives or scsi is just insane.

My peace is said for now and not sure what will do, how ever when friends ask about Linux ill suggest the Linux bible and let them decide on there on.

---

### Post by mcduck on 2008-07-18
> **NoJock said:**
> Thanks mcduck, i think the developers have lost there mind in a sense. Thy have broken some thing that worked. They want to change how thing work maybe it less work for them. Now you cant reference a Linux book or article on drive structure for Ubuntu now wants to be like Windows Vista and just put out a product thy like them selfs and thats it. I think this is a bug and if it the developers want to re wright the all the books published then they might as well do so. Ill stay with 7.10 for now and try the next one out and if it like the fish ( Hardy Heron ) might go some where else. Gusty Gibbon 7.10  just works and 8.04 is buggy by my standards and redevelopment does cause bug's and making all drives look like sata drives or scsi is just insane.

My peace is said for now and not sure what will do, how ever when friends ask about Linux ill suggest the Linux bible and let them decide on there on.
What is a bug? They decided to use the driver that gives you best performance. The only change to user is that if your disk used to be called /dev/hda it's now /dev/sda. Two letters have changed, we all get better performance and everything works just like before.

What difference does it make to you if the drive is called sdX instead of hdX?

It doesn't even change any guides or anything, at least not any good guides,a s any good guide to fstab will tell you to check what your drive/partition is called (with "fdisk -l" or some other command). Simply because nobody else will ever be able to tell that to you.

I think you are making a problem out of nothing. I can't imagine why..

---

### Post by NoJock on 2008-07-18
It a fish and it doesnt work like 5.04 ~ 7.10 have used them and still install on family and inlaws computer. Will not be up grading any of them till disk id is fixed.
All prior distros put the disks on the desk top and properly and hd1,hd2,sda1,sda2,and so forth. However the Heron is broken it doesnt and thats the way it is . Ill not be upgrading family or inlaws to 8.04 till it works.

---

### Post by mcduck on 2008-07-18
> **NoJock said:**
> It a fish and it doesnt work like 5.04 ~ 7.10 have used them and still install on family and inlaws computer. Will not be up grading any of them till disk id is fixed.
All prior distros put the disks on the desk top and properly and hd1,hd2,sda1,sda2,and so forth. However the Heron is broken it doesnt and thats the way it is . Ill not be upgrading family or inlaws to 8.04 till it works.

It's not going to be fixed, as its not a bug.

Besides, it's not ebvn "ubuntu-thing", many other distros have made the same change. and eventually the rest will follow.

So only thing you can do is to either live with it, or use the old Ubuntu version until it's support ends and then move back to Windows or OS X.

---

### Post by NoJock on 2008-07-18
Ok is there a way to fix the system so it boots and mounts the partitons and gives some referance that meening full other than 13.4 gig media?? Or can it just not be done any more??

---

### Post by mcduck on 2008-07-19
Sure. Actually it's done just like before, by adding a line to /etc/fstab. And even the old syntax works, if you want, but I recommend using the UUID to mount the partitions.

For example, /dev/sda4 seems to be a Windows partition that isn't mounted now. If you wanted it to automount at boot, and appear on your desktop as "Windows", this is how you'd do it:

1. Create the mount point for it: "sudo mkdir /media/Windows"

2. Open fstab for editing: "gksudo gedit /etc/fstab"

3. Add the following lines to the fstab file:
"UUID=47D9-C4D3 /media/Windows vfat user,fmask=0111,dmask=0000,utf8   0   0"

Alternatively, you can use the device name instead of the UUID, if you want: "/dev/sda4 /media/Windows vfat user,fmask=0111,dmask=0000,utf8   0   0"

4. save the file, and reboot. (or run "sudo mount -a")

You should look here for more info about fstab and mount options: [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")

Like I said, everything works just like before. The only thing you _have _ to do differently is replace "hdX" with "sdX".

The reason why I recommend using UUID instead of the device name is that UUID is unique identifier for the partition itself, and can thus be used even for removable drives, while the device names will change depending on the order in which the devices are recognized by the system. Becuase the device names of removable drives change, you can't configure the mounting of those drives in fstab unless you do it by UUID or label the partitions and use the label. And actually some motherboards and PATA/SATA controllers even detect internal drives in different order on every boot, which makes things rather difficult, but once again using UUID solves the problem.

The only bad thing about UUID is that if you edit your partitions, their UUID's will change and you need to change the fstab to use the new UUID.

---

### Post by mcduck on 2008-07-19
If the partitions are already auto-mountin correctly, only with names you don't like, you could of course just label the partitions. Then they would be mounted using the label as the name, instead of some generic "13.4 gig media".

Ext2/Ext3 partitions can be labeled with "e2label"-command.

I don't remeber the command used for FAT, and as I don't even have any NTFS partitions I have no idea how you'd label one in Linux. If youa re dual-booting you could just label the in Windows. Or install gParted and use that, it sould be able to label at least Linux-native and FAT partitions..

---

### Post by NoJock on 2008-07-19
Ok Sir (mcduck) that did not work and the drive will not even mount from computer now. What next Sir. Im open for almost any thing.

OK Sir neither one of the examples work, sorry. I still think some thing is broke. What shale i do now.

---

### Post by mcduck on 2008-07-20
Which partitions do you want mountd? And could you post here what you have in your fstab now (after trying to add the partition(s) there)?

---

### Post by NoJock on 2008-07-21
> **mcduck said:**
> Which partitions do you want mountd? And could you post here what you have in your fstab now (after trying to add the partition(s) there)?
mcduck, Thanks for your response. Would like to mount all and identafy with othere than ( drive size and media) built the folder in media and it still mounts
as 164.6 GB Media and not Windows. Not at all sure why file system is on sdf6 and swap is on sde3. Have only Two phisical drives hd0,0 eide wester digital and hd0,1 segate ata. Should be edie drive first and sata drive second this may be where all the problem is stemming from??

 lee@lee-ult:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sdf6
UUID=bdd2459c-5c25-4ea8-bba2-5f726644c3a0 /               ext3    relatime,errors=remount-ro 0       1

# /dev/sde3
UUID=c796e6b0-bac0-496f-b3b5-c131467eae8e none            swap    sw              0       0

# /dev/sda4
UUID=47D9-C4D3 /media/Windows vfat user,fmask=0111,dmask=0000,utf8 0 0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Anthony Fok on 2008-07-21
Hi NoJock,

First of all, note that the changes you are seeing is not unique to Ubuntu.  The libata kernel module is the way of the future, and it calls everything /dev/sd*X*.  Likewise, the "13.5 GB Media" is not Ubuntu specific either.  It is GNOME's new and user-friendly way of naming a device with no name (i.e. no label).

I suggest the following plan of action.

1. Please undo the changes to /etc/fstab that mcduck suggested.  (mcduck's suggestion is good, but it may be better to let GNOME volume manager figure out the volume name automatically.)

2. You have a dual-boot system right?  If so, boot into Windows, and label (rename) your C: Drive or D: drive to something else.

If your Windows partition(s) are NTFS, you could also "apt-get install ntfsprogs" and use ntfslabel to rename your drives.

This other thread about "Changing HD Name" may help: [http://ubuntuforums.org/showthread.php?p=4244863](http://ubuntuforums.org/showthread.php?p=4244863)

Cheers,

Anthony

---

### Post by NoJock on 2008-07-21
Anthony Fok, What i have is a multi boot situation. Windows Xp, Edubuntu 6.06
Ubuntu CE 7.04, Ubuntu 7.10, and now Ubuntu 8.04 That has problems. 

The two fat 32 drives are shared on a network for windows and myself on ubuntu. One is Audio and Video and the other drive is for Data storage.

All the other distros when booted auto load disks, I like that i can live with the hda1, hda2, sda1, and sda2 and so forth. the fact that all is changed is ok however is is not logical and is broken.

If only changed from hdx to sdx were true it would be workable but the whole structue is changed on my system.

lee@lee-ult:~$ cat /boot/grub/device.map
(hd0)	/dev/sde
(hd1)	/dev/sdf

This is the device map and it has my primary eide drive following the sata dive which is the second drive in my system. The boot up is just confusing as heck. Here is a copy of menu

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
# kopt=root=UUID=bdd2459c-5c25-4ea8-bba2-5f726644c3a0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=bdd2459c-5c25-4ea8-bba2-5f726644c3a0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=bdd2459c-5c25-4ea8-bba2-5f726644c3a0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bdd2459c-5c25-4ea8-bba2-5f726644c3a0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bdd2459c-5c25-4ea8-bba2-5f726644c3a0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde2.
title		Ubuntu, kernel 2.6.15-52-386 (on /dev/sde2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-52-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-52-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde2.
title		Ubuntu, kernel 2.6.15-52-386 (recovery mode) (on /dev/sde2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-52-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-52-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde2.
title		Ubuntu, kernel 2.6.15-51-386 (on /dev/sde2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-51-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde2.
title		Ubuntu, kernel 2.6.15-51-386 (recovery mode) (on /dev/sde2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-51-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde2.
title		Ubuntu, kernel 2.6.15-29-386 (on /dev/sde2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde2.
title		Ubuntu, kernel 2.6.15-29-386 (recovery mode) (on /dev/sde2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde2.
title		Ubuntu, kernel 2.6.15-28-386 (on /dev/sde2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde2.
title		Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/sde2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde2.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/sde2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde2.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/sde2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sde2.
title		Ubuntu, memtest86+ (on /dev/sde2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sdf1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=4f50d94a-9b75-46c4-9b18-b1cef1bcab5d ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sdf1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=4f50d94a-9b75-46c4-9b18-b1cef1bcab5d ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdf1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4f50d94a-9b75-46c4-9b18-b1cef1bcab5d ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdf1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4f50d94a-9b75-46c4-9b18-b1cef1bcab5d ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf1.
title		Ubuntu 7.10, memtest86+ (on /dev/sdf1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf5.
title		Ubuntu, kernel 2.6.20-17-generic (on /dev/sdf5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=d0451a7d-93c7-4674-bc7a-8bfb06c03967 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf5.
title		Ubuntu, kernel 2.6.20-17-generic (recovery mode) (on /dev/sdf5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=d0451a7d-93c7-4674-bc7a-8bfb06c03967 ro single 
initrd		/boot/initrd.img-2.6.20-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf5.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sdf5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d0451a7d-93c7-4674-bc7a-8bfb06c03967 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf5.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdf5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d0451a7d-93c7-4674-bc7a-8bfb06c03967 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf5.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sdf5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d0451a7d-93c7-4674-bc7a-8bfb06c03967 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf5.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdf5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d0451a7d-93c7-4674-bc7a-8bfb06c03967 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf5.
title		Ubuntu, memtest86+ (on /dev/sdf5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

They all work and work well. Im not sure if the problem is my computer or what but this is totaly a problem, it is not logical at all.

---

### Post by NoJock on 2008-07-23
Thanks to all looks like i confused every one. 

[SIZE="4"](Solved )[/SIZE] :lolflag:Thanks for all your help, I install the Ubuntu 64x and now the grub is logical again as well as my fstab. Have drives with names and everything.

Now lets see if Samba can be made to work.

---

