---
title: "[SOLVED] Not loading Grub - No Errors ?"
date: 2008-10-21
forum: Desktop Environments
---

### Post by gsingh on 2008-10-21
Hi, 

I've swapped my hard drive into a different PC, When i booted it up I went straight into the GRUB Command Line Interface.

I tried the following to fix:

grub> find /boot/grub/stage1
 (hd0,2)

grub> root (hd0,2)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

When i rebooted, I went straight into CLI.

The menu.lst had hd0,2, so thats correct.

Output of fdisk:
ubuntu@ubuntu:/media/disk$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x03430342

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/sda2       366137415   390716864    12289725    5  Extended
/dev/sda3        40965750   366137414   162585832+  83  Linux
/dev/sda5       366137478   390716864    12289693+  82  Linux swap / Solaris

Partition table entries are not in disk order


I've tried Live CD to run the find /boot/grub/stage1....but still get the CLI?

Tried Super Grub Disk, GNU/Linux > Automatically fix - doesn't fix.

Any ideas?

---

### Post by meierfra. on 2008-10-21
It seems that Grub cannot access menu.lst. To help diagnose the problem, boot from the Live CD and post the output of

```
sudo mount /dev/sda3 /mnt
cd /mnt/boot/grub
ls -l
cat menu.lst
```
(l in menu.lst is a lowercase L)

Also   at the Grub CLI (which you get when trying to boot into Ubuntu) type:

```

find /boot/grub/menu.lst
```

Post that output, too.

---

### Post by gsingh on 2008-10-22
thanks for the reply:

output as requested:

total 232
-rw-r--r-- 1 root root    197 2008-07-27 01:27 default
-rw-r--r-- 1 root root     15 2008-07-27 01:27 device.map
-rw-r--r-- 1 root root   8056 2008-07-27 01:27 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-07-27 01:27 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-07-27 01:27 installed-version
-rw-r--r-- 1 root root   8608 2008-07-27 01:27 jfs_stage1_5
-rw-r--r-- 1 root root   4666 2008-10-15 17:33 menu.lst
-rw-r--r-- 1 root root   4666 2008-10-15 17:17 menu.lst~
-rw-r--r-- 1 root root   4582 2008-08-10 17:54 menu.lst.backup
-rw-r--r-- 1 root root   4582 2008-08-10 17:24 menu.lst.old
-rw------- 1 root root      0 2008-10-20 21:20 menu.lst.save
-rw------- 1 root root   4661 2008-10-20 21:20 menu.lst.save.1
-rw-r--r-- 1 root root   7324 2008-07-27 01:27 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-07-27 01:27 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-08-10 17:58 splashimages
lrwxrwxrwx 1 root root     14 2008-08-10 17:46 splash.xpm.gz -> splash1.xpm.gz
-rw-r--r-- 1 root root    512 2008-07-27 01:27 stage1
-rw-r--r-- 1 root root 108356 2008-07-27 01:27 stage2
-rw-r--r-- 1 root root   9276 2008-07-27 01:27 xfs_stage1_5


Will try the second  part and get back to you shortly.

Thanks.

---

### Post by gsingh on 2008-10-22
the output of find /boot/grub/menu.lst = Error 15: File not found.

---

### Post by meierfra. on 2008-10-22
How old is your computer? Some bios can only see the first 137GB of a hard drive.  Your Ubuntu partitions starts at about 20GB and ends at 180 GB. So Grub's stage2 file is probably within the first 137GB of the hard drive, but menu.lst is not. To confirm this,  boot from the live CD, open terminal and post the output of 


```
sudo grub
```
and at the grub prompt:


```
root (hd0,2)
blocklist /boot/grub/menu.lst
blocklist /boot/grub/stage2
```

Just to make sure that nothing is wrong  with the file "menu.lst" could you post  your  "menu.lst" (see my last post for instruction, you didn't  do the "cat menu.lst" part yet)


To cure the problem, I suggest to create a separate boot partition. Just follow these [ instruction ]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition")  from Hermanzone. 

 To avoid problems with XP, I would  shrink the Ubuntu partition on the left side and create the boot partition just before the Ubuntu partition, leaving the XP partition untouched. Let me know if you need more detailed help.

---

### Post by gsingh on 2008-10-22
Output of menu.lst

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
color cyan/blue white/blue

#A splash image for the menu
#splashimage=(hd0,4)/boot/grub/splashimages/splash1.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=4feab736-f890-4fc4-9827-96392cc5e468 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4feab736-f890-4fc4-9827-96392cc5e468 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4feab736-f890-4fc4-9827-96392cc5e468 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
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



====================
Out of the commands:

grub> root (hd0,2) 

grub> blocklist /boot/grub/menu.lst
(hd0,2)276408608+8,276437072+2

grub> blocklist /boot/grub/stage2  
(hd0,2)98451456+96,98451560+116

Any issues?  with the above?


The PC is 6+ years old!
I will follow the guide as requested to create a new boot partition and let you know how i get on.

---

### Post by meierfra. on 2008-10-22
> Any issues? with the above?

No, everything came out the way I expected. stage2 is  at 70GB inside the 137GB limit. menu.lst is at 160GB, just outside the 137 GB. 

So I'm confident that creating a separate boot partition will solve your problem.

---

### Post by gsingh on 2008-10-23
thanks meierfra, your suggestion fixed the issue.

Back on line!

---

