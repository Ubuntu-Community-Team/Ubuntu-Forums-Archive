---
title: "Ubuntu 8.10 Install"
date: 2008-12-22
forum: General Help
---

### Post by Xarver on 2008-12-22
Hi, I had Windows XP and Opensuse on my computer,
but I wanted to replace Opensuse with Ubuntu 8.10.
I burned a cd, and when through the installation process,
although when I restarted the computer openSuse was still there.
Is there any way to remove opensuse and transfer the disk space to ubuntu,
and also keep Windows XP?

Apparently opensuse is in /dev/sda6
The opensuse option shows in the GRUB boot loader.
I want to remove opensuse and keep Ubuntu and Windows, without having to do the whole installation process again.

Any help appreciated. :)

---

### Post by caljohnsmith on 2008-12-22
It sounds like you might have installed Ubuntu to other partitions rather than on top of OpenSUSE. If you use Ubuntu's Partition Editor "gparted" (System > Admin > Partition Editor from the Live CD), you could maybe delete your OpenSUSE partitions and let the Ubuntu partition take over that space. It depends though on the physical layout of your partitions. How about opening a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -lu
```
And please identify your OpenSUSE and Ubuntu partitions.

---

### Post by LoneWolfJack on 2008-12-22
If opensuse has its own partition (which it probably does), you can install gparted (it's in the repos) and use it to delete the opensuse partition and/or assign the space to the ubuntu partition.

---

### Post by Xarver on 2008-12-22
Here is my output:
> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca09ca09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    33222419    16611178+   7  HPFS/NTFS
/dev/sda2        33222420    57352049    12064815    f  W95 Ext'd (LBA)
/dev/sda3        57352050    78124094    10386022+   7  HPFS/NTFS
/dev/sda5        56227563    57352049      562243+  82  Linux swap / Solaris
/dev/sda6        33222546    43712864     5245159+  83  Linux
/dev/sda7        43712928    46668824     1477948+  83  Linux
/dev/sda8        46668888    55697354     4514233+  83  Linux
/dev/sda9        55697418    56227499      265041   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1015 MB, 1015021568 bytes
255 heads, 63 sectors/track, 123 cylinders, total 1982464 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x434f4475

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     1981727      990832+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(941, 254, 63) logical=(123, 90, 63)

/dev/sda1 is Windows XP
/dev/sda6 I'm thinking is Opensuse
And I don't know the rest.
I'm not that good in linux. *Yet*

So if I install gparted, you guys can tell me how to do this? :)

~ Xarver

---

### Post by caljohnsmith on 2008-12-22
Since we don't know yet which of your partitions is OpenSUSE or Ubuntu, how about doing the following:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and which is your OpenSUSE and Ubuntu partitions.

---

### Post by cariboo on 2008-12-22
Can you boot into Ubuntu? If so you can just remove the Opensusse entry from grub. To edit grub press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

If you can't boot into Ubuntu could you paste the output of:

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```

The above commands must be run in a terminal.

Jim

---

### Post by nordmichael29 on 2008-12-22
If I understand correctly that you want to remove opensuse and all it's files, (and consequently all files stored on the partition) start gparted (or install it first) and it has a very good GUI just make sure to mount the partitions you don't want to remove, and then remove the opensuse partition.

---

### Post by Xarver on 2008-12-22
Yes, I'm on ubuntu right now but opensuse still has it's own partition.
Here's the output:
```
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #8 for its boot files.
No known boot loader is installed in the MBR of /dev/sdb

sda1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 63.
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM

sda2:
    File system:  Extended Partition

sda3:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sda3 starts at sector 57352050.
    Operating System: 
    Boot files/directories present: 

sda5:
    File system:  swap

sda6:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System:  Welcome to openSUSE 11.0 (i586) - Kernel \r (\l).
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda8:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda9:
    File system:  swap

sdb1:
    File system:  vfat
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca09ca09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    33222419    16611178+   7  HPFS/NTFS
/dev/sda2        33222420    57352049    12064815    f  W95 Ext'd (LBA)
/dev/sda3        57352050    78124094    10386022+   7  HPFS/NTFS
/dev/sda5        56227563    57352049      562243+  82  Linux swap / Solaris
/dev/sda6        33222546    43712864     5245159+  83  Linux
/dev/sda7        43712928    46668824     1477948+  83  Linux
/dev/sda8        46668888    55697354     4514233+  83  Linux
/dev/sda9        55697418    56227499      265041   82  Linux swap / Solaris

Partition table entries are not in disk order

Warning: partition 5 does not start at a cylinder boundary


Disk /dev/sdb: 1015 MB, 1015021568 bytes
255 heads, 63 sectors/track, 123 cylinders, total 1982464 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x434f4475

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     1981727      990832+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(941, 254, 63) logical=(123, 90, 63)

Warning: partition 5 does not start at a cylinder boundary
Warning: partition 1 extends past end of disk

/dev/sda1: UUID="A428F17928F14AB6" TYPE="ntfs" 
/dev/sda3: UUID="5AF07CE0F07CC433" LABEL="Disk" TYPE="ntfs" 
/dev/sda5: UUID="9950da98-3a99-43d0-a202-70db9526e9b1" TYPE="swap" 
/dev/sda6: UUID="5f31937f-fab2-4edf-b5ea-41264ff4dcdf" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="c7f8d14c-8719-434b-ad3b-b457b0db53d3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="d97fd567-65d9-454b-a12e-a60ac990f153" TYPE="ext3" 
/dev/sda9: UUID="d394dd12-da37-4906-9a96-f36413902275" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" UUID="0000-02B7" TYPE="vfat" 

sda1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


sda6/boot/grub/menu.lst

# Modified by YaST2. Last modification on Tue Nov 25 19:26:24 PST 2008
default 0
timeout 8
gfxmenu (hd0,5)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0 - 2.6.25.18-0.2
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.25.18-0.2-default root=/dev/disk/by-id/scsi-SATA_HTS541040G9AT00_MPB2L0X2CAXWMG-part6 resume=/dev/sda5 splash=silent showopts vga=0x317
    initrd /boot/initrd-2.6.25.18-0.2-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0 - 2.6.25.18-0.2
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.25.18-0.2-default root=/dev/disk/by-id/scsi-SATA_HTS541040G9AT00_MPB2L0X2CAXWMG-part6 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x317
    initrd /boot/initrd-2.6.25.18-0.2-default

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,5)
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd0,5)
    chainloader (hd0,2)+1

sda6/etc/fstab

/dev/disk/by-id/scsi-SATA_HTS541040G9AT00_MPB2L0X2CAXWMG-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/scsi-SATA_HTS541040G9AT00_MPB2L0X2CAXWMG-part6 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/scsi-SATA_HTS541040G9AT00_MPB2L0X2CAXWMG-part7 /home                ext3       acl,user_xattr        1 2
/dev/disk/by-id/scsi-SATA_HTS541040G9AT00_MPB2L0X2CAXWMG-part1 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/scsi-SATA_HTS541040G9AT00_MPB2L0X2CAXWMG-part3 /windows/D           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

sda6/boot

total 12720
drwxr-xr-x  3 root root    4096 2008-12-14 11:35 .
drwxr-xr-x 21 root root    4096 2008-12-21 09:08 ..
-rw-------  1 root root     512 2008-11-17 05:59 backup_mbr
lrwxrwxrwx  1 root root       1 2008-11-17 05:55 boot -> .
-rw-r--r--  1 root root   88815 2008-10-22 08:45 config-2.6.25.18-0.2-default
drwxr-xr-x  2 root root    4096 2008-11-25 19:26 grub
lrwxrwxrwx  1 root root      28 2008-11-25 19:26 initrd -> initrd-2.6.25.18-0.2-default
-rw-r--r--  1 root root 5746782 2008-11-25 19:26 initrd-2.6.25.18-0.2-default
-rw-r--r--  1 root root  115828 2008-06-06 17:38 memtest.bin
-rw-r--r--  1 root root  428544 2008-12-14 11:35 message
-rw-r--r--  1 root root  198790 2008-10-22 08:46 symsets-2.6.25.18-0.2-default.tar.gz
-rw-r--r--  1 root root  444548 2008-10-22 08:46 symtypes-2.6.25.18-0.2-default.gz
-rw-r--r--  1 root root  129301 2008-10-22 08:46 symvers-2.6.25.18-0.2-default.gz
-rw-r--r--  1 root root  923869 2008-10-22 08:37 System.map-2.6.25.18-0.2-default
-rw-r--r--  1 root root 2734956 2008-10-22 08:45 vmlinux-2.6.25.18-0.2-default.gz
lrwxrwxrwx  1 root root      29 2008-11-25 19:25 vmlinuz -> vmlinuz-2.6.25.18-0.2-default
-rw-r--r--  1 root root 2128896 2008-10-22 08:38 vmlinuz-2.6.25.18-0.2-default

sda6/boot/grub

total 232
drwxr-xr-x 2 root root   4096 2008-11-25 19:26 .
drwxr-xr-x 3 root root   4096 2008-12-14 11:35 ..
-rw------- 1 root root     10 2008-11-25 15:39 default
-rw------- 1 root root     15 2008-11-17 05:59 device.map
-rw-r--r-- 1 root root     14 2008-11-17 05:45 device.map.old
-rw-r--r-- 1 root root   7596 2008-06-06 12:52 e2fs_stage1_5
-rw-r--r-- 1 root root   7328 2008-06-06 12:52 fat_stage1_5
-rw-r--r-- 1 root root   6604 2008-06-06 12:52 ffs_stage1_5
-rw-r--r-- 1 root root   6600 2008-06-06 12:52 iso9660_stage1_5
-rw-r--r-- 1 root root   8268 2008-06-06 12:52 jfs_stage1_5
-rw------- 1 root root   1149 2008-11-25 19:26 menu.lst
-rw------- 1 root root   1894 2008-11-25 19:26 menu.lst.old
-rw-r--r-- 1 root root   6832 2008-06-06 12:52 minix_stage1_5
-rw-r--r-- 1 root root   9216 2008-06-06 12:52 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-06-06 12:52 stage1
-rw-r--r-- 1 root root 105630 2008-11-17 05:59 stage2
-rw-r--r-- 1 root root   6864 2008-06-06 12:52 ufs2_stage1_5
-rw-r--r-- 1 root root   6204 2008-06-06 12:52 vstafs_stage1_5
-rw-r--r-- 1 root root   9028 2008-06-06 12:52 xfs_stage1_5

sda8/boot/grub/menu.lst

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
# kopt=root=UUID=d97fd567-65d9-454b-a12e-a60ac990f153 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d97fd567-65d9-454b-a12e-a60ac990f153

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d97fd567-65d9-454b-a12e-a60ac990f153
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d97fd567-65d9-454b-a12e-a60ac990f153 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d97fd567-65d9-454b-a12e-a60ac990f153
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d97fd567-65d9-454b-a12e-a60ac990f153 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d97fd567-65d9-454b-a12e-a60ac990f153
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		openSUSE 11.0 - 2.6.25.18-0.2 (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.25.18-0.2-default root=/dev/disk/by-id/scsi-SATA_HTS541040G9AT00_MPB2L0X2CAXWMG-part6 resume=/dev/sda5 splash=silent showopts vga=0x317 
initrd		/boot/initrd-2.6.25.18-0.2-default
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Failsafe -- openSUSE 11.0 - 2.6.25.18-0.2 (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.25.18-0.2-default root=/dev/disk/by-id/scsi-SATA_HTS541040G9AT00_MPB2L0X2CAXWMG-part6 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x317 
initrd		/boot/initrd-2.6.25.18-0.2-default
savedefault
boot


sda8/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=d97fd567-65d9-454b-a12e-a60ac990f153 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=d394dd12-da37-4906-9a96-f36413902275 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda8/boot

total 15760
drwxr-xr-x  3 root root    4096 2008-12-22 09:54 .
drwxr-xr-x 20 root root    4096 2008-12-22 09:21 ..
-rw-r--r--  1 root root  507665 2008-11-04 13:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 15:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 13:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 15:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-22 09:54 grub
-rw-r--r--  1 root root 8182444 2008-12-22 09:21 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 13:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 13:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 15:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 13:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 15:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 13:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 15:46 vmlinuz-2.6.27-9-generic

sda8/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-22 09:54 .
drwxr-xr-x 3 root root   4096 2008-12-22 09:54 ..
-rw-r--r-- 1 root root    197 2008-12-22 09:22 default
-rw-r--r-- 1 root root     15 2008-12-22 09:22 device.map
-rw-r--r-- 1 root root   8108 2008-12-22 09:22 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-22 09:22 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-22 09:22 installed-version
-rw-r--r-- 1 root root   8712 2008-12-22 09:22 jfs_stage1_5
-rw-r--r-- 1 root root   5479 2008-12-22 09:54 menu.lst
-rw-r--r-- 1 root root   5479 2008-12-22 09:54 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-22 09:22 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-22 09:22 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-22 09:22 stage1
-rw-r--r-- 1 root root 121460 2008-12-22 09:22 stage2
-rw-r--r-- 1 root root   9556 2008-12-22 09:22 xfs_stage1_5

StdErr Messages 

Unknown MBR on /dev/sdb

00000000  fa 33 c0 8e d8 8e c0 8e  d0 bc fc 7b fb fc be 00  |.3.........{....|
00000010  7c bf 00 80 b9 80 00 f3  66 a5 ea 1f 80 00 00 80  ||.......f.......|
00000020  26 ce 81 80 0f 85 07 01  80 26 de 81 80 0f 85 fe  |&........&......|
00000030  00 80 26 ee 81 80 0f 85  f5 00 be be 81 e8 04 00  |..&.............|
00000040  cd 18 eb fe 8a 04 24 80  75 01 c3 66 8b 44 08 e8  |......$.u..f.D..|
00000050  8d 00 88 44 01 89 5c 02  60 bb 00 7c b8 00 00 8e  |...D..\.`..|....|
00000060  c0 8b 4c 02 8a 74 01 b8  01 02 cd 13 0f 82 c4 00  |..L..t..........|
00000070  81 3e fe 7d 55 aa 0f 85  bf 00 61 60 33 ff 8e c7  |.>.}U.....a`3...|
00000080  b4 08 cd 13 83 e1 3f 8a  d6 b6 00 42 66 c1 e2 10  |......?....Bf...|
00000090  8b d1 66 39 16 18 7c 66  89 16 18 7c 61 0f 95 c0  |..f9..|f...|a...|
000000a0  bf 24 7c 66 81 3e 03 7c  4e 54 46 53 74 0b 66 83  |.$|f.>.|NTFSt.f.|
000000b0  3e 11 7c 00 75 03 bf 40  7c 8a e2 86 25 38 d4 74  |>.|.u..@|...%8.t|
000000c0  04 3c 01 75 15 52 bb 00  7c b8 00 00 8e c0 8b 4c  |.<.u.R..|......L|
000000d0  02 8a 74 01 b8 01 03 cd  13 5a ea 00 7c 00 00 1e  |..t......Z..|...|
000000e0  52 56 66 50 33 ff 8e c7  b4 08 cd 13 83 e1 3f 0f  |RVfP3.........?.|
000000f0  b6 c6 40 f7 e1 66 0f b7  d8 66 58 66 33 d2 66 f7  |..@..f...fXf3.f.|
00000100  f3 8b e8 8b c2 33 d2 f7  f1 fe c2 8b cd 8a da 8a  |.....3..........|
00000110  fd c0 e3 02 c1 eb 02 8a  f9 5e 5a 1f c3 ac 3c 00  |.........^Z...<.|
00000120  74 0b 56 bb 07 00 b4 0e  cd 10 5e eb f0 eb fe be  |t.V.......^.....|
00000130  3e 81 eb e9 be 56 81 eb  e4 be 75 81 eb df 49 6e  |>....V....u...In|
00000140  76 61 6c 69 64 20 70 61  72 74 69 74 69 6f 6e 20  |valid partition |
00000150  74 61 62 6c 65 00 45 72  72 6f 72 20 6c 6f 61 64  |table.Error load|
00000160  69 6e 67 20 6f 70 65 72  61 74 69 6e 67 20 73 79  |ing operating sy|
00000170  73 74 65 6d 00 4d 69 73  73 69 6e 67 20 6f 70 65  |stem.Missing ope|
00000180  72 61 74 69 6e 67 20 73  79 73 74 65 6d 00 00 00  |rating system...|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  75 44 4f 43 00 00 80 01  |.....,DcuDOC....|
000001c0  01 00 06 fe ff ad 3f 00  00 00 e1 3c 1e 00 00 00  |......?....<....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on /dev/sdb1

00000000  eb 3c 90 6d 6b 64 6f 73  66 73 00 00 02 20 04 00  |.<.mkdosfs... ..|
00000010  02 00 02 00 00 f8 f2 00  3d 00 20 00 3f 00 00 00  |........=. .?...|
00000020  e0 3c 1e 00 00 00 29 b7  02 00 00 20 20 20 20 20  |.<....)....     |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 0e 1f  |      FAT16   ..|
00000040  be 5b 7c ac 22 c0 74 0b  56 b4 0e bb 07 00 cd 10  |.[|.".t.V.......|
00000050  5e eb f0 32 e4 cd 16 cd  19 eb fe 54 68 69 73 20  |^..2.......This |
00000060  69 73 20 6e 6f 74 20 61  20 62 6f 6f 74 61 62 6c  |is not a bootabl|
00000070  65 20 64 69 73 6b 2e 20  20 50 6c 65 61 73 65 20  |e disk.  Please |
00000080  69 6e 73 65 72 74 20 61  20 62 6f 6f 74 61 62 6c  |insert a bootabl|
00000090  65 20 66 6c 6f 70 70 79  20 61 6e 64 0d 0a 70 72  |e floppy and..pr|
000000a0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 74  |ess any key to t|
000000b0  72 79 20 61 67 61 69 6e  20 2e 2e 2e 20 0d 0a 00  |ry again ... ...|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

~ Xarver

---

### Post by caljohnsmith on 2008-12-22
OK, so OpenSUSE is on sda6 while Ubuntu is on sda8 it looks like. You also have two swap partitions when you actually only need one. Since Ubuntu is a new installation, how about using gparted to delete partitions sda6 through sda9, and then create whichever partitions you want for Ubuntu with that space, along with a swap partition. After that, reinstall Ubuntu to the partitions you create. I think that would make alot more sense than trying to resize and delete your existing partitions, and then you would have to modify a bunch of Ubuntu's system files too. How about trying that and let us know how it goes.

---

### Post by Xarver on 2008-12-22
Ok, just to make sure, this is what I do:
Delete partitions sda6 through sda9, create partitions, and redo the ubuntu install?

Isn't there a way to just uninstall openSuse and keep Ubuntu and Windows
without having to go through the whole 20-60min process? :P

~ Xarver

---

### Post by caljohnsmith on 2008-12-22
> **Xarver said:**
> Ok, just to make sure, this is what I do:
Delete partitions sda6 through sda9, create partitions, and redo the ubuntu install?

Isn't there a way to just uninstall openSuse and keep Ubuntu and Windows
without having to go through the whole 20-60min process? :P

~ Xarver
It's up to you; Grub on start up is currently controlled by the Ubuntu sda8 partition, so if you want to simply delete the sda6 OpenSUSE partition, you can certainly do that. But if you resize Ubuntu's partition to take over that space, you will have alot of reconfiguring to do, because the partition number and UUID will change. In that case, reinstalling would be alot more simple I think. And yes, you have it right, I would delete sda6 through sda9 and reinstall Ubuntu if I were you.

---

### Post by Xarver on 2008-12-22
Ok, thanks, so I just delete sda 6 - sda9 with gparted on ubuntu, put the livecd in,
restart the computer, and reinstall? :)

Just making sure. If it's solved, I'm going to mark this thread as *solved*

EDIT:
Important:
For some reason it won't let me delete sda 6
I can't delete any partitions...
Even though I am the *admin* user.
Help? :|

---

### Post by caljohnsmith on 2008-12-22
When you are in gparted, try right-clicking your swap partitions and select "swapoff". After that try deleting your partitions, and let me know how it goes.

---

### Post by Xarver on 2008-12-22
I only have the ability to delete /dev/sda9
Out of 6-9.
If I try to delete 6,7, or 9 I get an error message:
"Unable to delete /dev/sda6!
Please unmount any logical partitions having a number higher than 6"

So in other words, I can only delete the swap drives...

---

### Post by caljohnsmith on 2008-12-22
OK, from the command line try:
```
sudo umount -a
```
And then try again. If that doesn't work, reboot the Live CD again, and open up gparted with:
```
gksudo gparted 
```
And try deleting the partitions again (make sure to "swapoff" the swap partitions first), and if you get any errors in the terminal, copy/paste them back here.

---

### Post by Xarver on 2008-12-22
Ok, I deleted sda6-9 and hopefully the install goes well.
Thanks. :)

---

