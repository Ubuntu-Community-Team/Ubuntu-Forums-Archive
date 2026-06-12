---
title: "GRUB  ultimate edition 2.0 - gfxmenu - gfxboot bootloader configuration problem !..."
date: 2009-01-16
forum: General Help
---

### Post by Siracide on 2009-01-16
I am trying to customize my GRUB as Suse. The main problem is that is not working at all; I did follow the steps from the following thread:

[http://technoemperor.blogspot.com/2008/10/installing-gfx-grub-in-ubuntu-grub.html](http://technoemperor.blogspot.com/2008/10/installing-gfx-grub-in-ubuntu-grub.html)

Then it is still showing the same thing... black screen with menus on it...

Then also I did try to get a GRUB bootloader editor as startup manager which it did work fine but allowing me only to have my menu with a background with less than 256 colors in depth, which it really sucks...

I did use also KGRUB editor, but nothing changed, and it did give me the same result as the above program I mentioned.

Now, after messing around with my GRUB I have not found anything that would be helpful to setup a very nice menu starter like the ones suse has... i.e. gfx /boot/grub/message.ubugrey

I've found that some of the messages appear to be corrupted while surfing and downloading them from the web...

Now, after some google skills, I've found a script which I do not know what it exactly means that allowed me to get my setup information, and if somebody would help me!..

I am kind of beginner on this... :( ... I would like to have my message.xyz like the ones suse has... but in ubuntu... Thanks...
> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc0229cdb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    13365247     6681600   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2        13365248   342361214   164497983+   7  HPFS/NTFS
/dev/sda3       386797005   390716864     1959930    5  Extended
/dev/sda4   *   342361215   386797004    22217895   83  Linux
/dev/sda5       386813070   390716864     1951897+  82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: partition 1 does not end at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="3C9897B398976A62" TYPE="ntfs" 
/dev/sda2: UUID="F0F49A0CF499D566" TYPE="ntfs" 
/dev/sda4: UUID="ebef8ac4-b999-4907-917a-4975b635c5fd" TYPE="ext3" 
/dev/sda5: UUID="1f05ca3c-0ad7-4663-b34e-8648ff889f64" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/skyangelo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=skyangelo)

================================== sda1/boot: ==================================

total 3372
drwxrwxrwx 1 root root       0 2009-01-11 10:13 .
drwxrwxrwx 1 root root    4096 2008-10-13 21:59 ..
-rwxrwxrwx 1 root root  262144 2009-01-11 10:13 bcd
-rwxrwxrwx 1 root root    9216 2009-01-11 10:13 BCD.LOG
-rwxrwxrwx 1 root root 3170304 2006-09-18 16:45 boot.sdi
-rwxrwxrwx 1 root root    2048 2006-09-18 16:27 etfsboot.com
drwxrwxrwx 1 root root       0 2006-11-29 13:17 fonts

================================== sda2/Boot: ==================================

total 772
drwxrwxrwx 1 root root   4096 2008-09-28 15:34 .
drwxrwxrwx 1 root root  20480 2009-01-14 09:01 ..
-rwxrwxrwx 1 root root  28672 2009-01-15 00:54 BCD
-rwxrwxrwx 1 root root 262144 2009-01-15 00:52 BCD.LOG
-rwxrwxrwx 2 root root      0 2007-01-09 13:11 BCD.LOG1
-rwxrwxrwx 2 root root      0 2007-01-09 13:11 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2007-01-09 13:11 bootstat.dat
drwxrwxrwx 1 root root      0 2008-09-28 15:34 cs-CZ
drwxrwxrwx 1 root root      0 2008-09-28 15:34 da-DK
drwxrwxrwx 1 root root      0 2008-09-28 15:34 de-DE
drwxrwxrwx 1 root root      0 2008-09-28 15:34 el-GR
drwxrwxrwx 1 root root      0 2008-09-28 15:34 en-US
drwxrwxrwx 1 root root      0 2008-09-28 15:34 es-ES
drwxrwxrwx 1 root root      0 2008-09-28 15:34 fi-FI
drwxrwxrwx 1 root root      0 2008-09-28 15:34 Fonts
drwxrwxrwx 1 root root      0 2008-09-28 15:34 fr-FR
drwxrwxrwx 1 root root      0 2008-09-28 15:34 hu-HU
drwxrwxrwx 1 root root      0 2008-09-28 15:34 it-IT
drwxrwxrwx 1 root root      0 2008-09-28 15:34 ja-JP
drwxrwxrwx 1 root root      0 2008-09-28 15:34 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 01:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-09-28 15:34 nb-NO
drwxrwxrwx 1 root root      0 2008-09-28 15:34 nl-NL
drwxrwxrwx 1 root root      0 2008-09-28 15:34 pl-PL
drwxrwxrwx 1 root root      0 2008-09-28 15:34 pt-BR
drwxrwxrwx 1 root root      0 2008-09-28 15:34 pt-PT
drwxrwxrwx 1 root root      0 2008-09-28 15:34 ru-RU
drwxrwxrwx 1 root root      0 2008-09-28 15:34 sv-SE
drwxrwxrwx 1 root root      0 2008-09-28 15:34 tr-TR
drwxrwxrwx 1 root root      0 2008-09-28 15:34 zh-CN
drwxrwxrwx 1 root root      0 2008-09-28 15:34 zh-HK
drwxrwxrwx 1 root root      0 2008-09-28 15:34 zh-TW

=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ebef8ac4-b999-4907-917a-4975b635c5fd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ebef8ac4-b999-4907-917a-4975b635c5fd

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		ebef8ac4-b999-4907-917a-4975b635c5fd
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ebef8ac4-b999-4907-917a-4975b635c5fd ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ebef8ac4-b999-4907-917a-4975b635c5fd
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ebef8ac4-b999-4907-917a-4975b635c5fd ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ebef8ac4-b999-4907-917a-4975b635c5fd
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ebef8ac4-b999-4907-917a-4975b635c5fd ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ebef8ac4-b999-4907-917a-4975b635c5fd
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ebef8ac4-b999-4907-917a-4975b635c5fd ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ebef8ac4-b999-4907-917a-4975b635c5fd
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=ebef8ac4-b999-4907-917a-4975b635c5fd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1f05ca3c-0ad7-4663-b34e-8648ff889f64 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda4/boot: ==================================

total 26848
drwxr-xr-x  3 root root     4096 2009-01-16 08:36 .
drwxr-xr-x 21 root root     4096 2009-01-15 13:49 ..
-rw-r--r--  1 root root   507665 2008-11-04 15:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root   507665 2008-11-20 17:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root    91364 2008-11-04 15:00 config-2.6.27-7-generic
-rw-r--r--  1 root root    91364 2008-11-20 17:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root     4096 2009-01-16 08:29 grub
-rw-r--r--  1 root root  8984132 2009-01-16 08:07 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 10527050 2009-01-16 08:36 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root   124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root  1029585 2008-11-04 15:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root  1029585 2008-11-20 17:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root     1073 2008-11-04 15:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root     1073 2008-11-20 17:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root  2244272 2008-10-24 03:29 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root  2244304 2008-11-20 17:46 vmlinuz-2.6.27-9-generic

=============================== sda4/boot/grub: ===============================

total 252
drwxr-xr-x 3 root root        4096 2009-01-16 08:29 .
drwxr-xr-x 3 root root        4096 2009-01-16 08:36 ..
-rw-r--r-- 1 root root         197 2009-01-15 13:14 default
-rw-r--r-- 1 root root          15 2009-01-15 13:14 device.map
-rw-r--r-- 1 root root        8108 2009-01-15 13:14 e2fs_stage1_5
-rw-r--r-- 1 root root        7856 2009-01-15 13:14 fat_stage1_5
-rw-r--r-- 1 root root          16 2009-01-15 13:14 installed-version
-rw-r--r-- 1 root root        8712 2009-01-15 13:14 jfs_stage1_5
-rw------- 1 root root        5285 2009-01-16 09:40 menu.lst
-rw-r--r-- 1 root root        5285 2009-01-16 08:29 menu.lst~
-rw-r--r-- 1 root root        5285 2009-01-15 13:49 menu.lst.090115163844
-rw------- 1 root root        5285 2009-01-16 08:02 menu.lst.backup
-rw------- 1 root root        5285 2009-01-15 18:44 menu.lst_original
-rw-r--r-- 1 root root        7352 2009-01-15 13:14 minix_stage1_5
-rw-r--r-- 1 root root        9756 2009-01-15 13:14 reiserfs_stage1_5
drwxrwxr-x 2 root skyangelo   4096 2009-01-16 08:34 splashimages
-rw-r--r-- 1 root root         512 2009-01-15 13:14 stage1
-rw-r--r-- 1 root root      121460 2009-01-15 13:14 stage2
-rw-r--r-- 1 root root        9556 2009-01-15 13:14 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

---

