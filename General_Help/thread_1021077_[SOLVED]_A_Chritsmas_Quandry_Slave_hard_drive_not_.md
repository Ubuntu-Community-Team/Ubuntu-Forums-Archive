---
title: "[SOLVED] A Chritsmas Quandry: Slave hard drive not recognized"
date: 2008-12-24
forum: General Help
---

### Post by winrowc on 2008-12-24
Im getting GRUB Error 17 after fixing a grub error 18, becuase my second hard drive was too big for my mobo. 

I have two hard drives, a 80 gb with a 500mb partition for booting, and that hard drive has ubuntu on it. I have a second 150 gb drive, which has windows on it, but isn't recognized by ubuntu with the live cd and just gives me a GRUB error 17 if i try to boot up ubuntu normally, which works fine without the slave drive (150gb) connected.My bios recognizes them as primary IDE master and slave drives, so I assume they are setup properly in that regard. Can someone help me get ubuntu to recognize my slave drive? Thanks, and Merry Christmas!

---

### Post by dcstar on 2008-12-25
> **winrowc said:**
> Im getting GRUB Error 17 after fixing a grub error 18, becuase my second hard drive was too big for my mobo. 

I have two hard drives, a 80 gb with a 500mb partition for booting, and that hard drive has ubuntu on it. I have a second 150 gb drive, which has windows on it, but isn't recognized by ubuntu with the live cd and just gives me a GRUB error 17 if i try to boot up ubuntu normally, which works fine without the slave drive (150gb) connected.My bios recognizes them as primary IDE master and slave drives, so I assume they are setup properly in that regard. Can someone help me get ubuntu to recognize my slave drive? Thanks, and Merry Christmas!

Double check all Master/Slave settings on all devices, make sure that any IDE channel has a Master device on it and not just a Slave.

---

### Post by wolfen69 on 2008-12-25
Grub error 17 : Cannot mount selected partition. This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

maybe something happened to your windows install?

---

### Post by winrowc on 2008-12-25
> **dcstar said:**
> Double check all Master/Slave settings on all devices, make sure that any IDE channel has a Master device on it and not just a Slave.

What do you mean? When I look in the BIos settings it says
Primary IDE Master Harddisk
Primary IDE Slave Harddisk

---

### Post by winrowc on 2008-12-25
Do you think if i wiped the windows hard drive and then tried it would work? Shouldn't it at least recognize that theres a drive in the Partition Editor on the live cd, even if its  a different file system than Linux can use?

---

### Post by winrowc on 2008-12-25
So I tried everything suggested here, and wiped the drive clean, but still nothing. Any other suggestions to get this drive recognized?

---

### Post by dcstar on 2008-12-26
> **winrowc said:**
> What do you mean? When I look in the BIos settings it says
Primary IDE Master Harddisk
Primary IDE Slave Harddisk

Check the DRIVES - look at them and see what the settings are.

---

### Post by caljohnsmith on 2008-12-26
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by winrowc on 2008-12-27
I guess it was a problem with the hard drive jumper. Now my windows hard drive is recognized as media when i look at the drives. Can I get anything off this drive now, or do I have to reformat it since its NTSF?


Here's the RESULTS,txt

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for its boot files.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Mounting failed:  
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 sdb1 ntfs-3g force 0 0

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf44ff44f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149211719    74605828+  83  Linux
/dev/sda2       150255945   156296384     3020220    5  Extended
/dev/sda3       149211720   150255944      522112+  83  Linux
/dev/sda5       150256008   156296384     3020188+  82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe2f1cb9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   312578047   156288000    7  HPFS/NTFS

sfdisk -V /dev/sdb:

/dev/sda: OK
Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="e233827f-fb63-4847-b116-6c58e06a54b6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="73bb1887-d6a1-41d8-be7a-a7e175f6514a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="cfcf53bd-2a80-4e41-abce-4fe8453fed88" TYPE="swap" 
/dev/sdb1: UUID="44289F99289F8916" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-8-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/boot/initrd.img-2.6.27-8-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-6-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-6-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-6-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/boot/initrd.img-2.6.27-6-generic

title		Ubuntu 8.10, kernel 2.6.27-4-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-4-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu 8.10, kernel 2.6.27-3-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-3-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-3-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-3-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-3-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/boot/initrd.img-2.6.27-3-generic

title		Ubuntu 8.10, kernel 2.6.27-2-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-2-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-2-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-2-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-2-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/boot/initrd.img-2.6.27-2-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=73bb1887-d6a1-41d8-be7a-a7e175f6514a /boot
ext3 defaults,errors=remount-ro 0        1
# /dev/sda1
UUID=e233827f-fb63-4847-b116-6c58e06a54b6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=cfcf53bd-2a80-4e41-abce-4fe8453fed88 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=127,devmode=664 0 0

================================== sda1/boot: ==================================

total 94384
drwxr-xr-x  3 root root    4096 2008-12-21 17:14 .
drwxr-xr-x 20 root root    4096 2008-12-27 14:28 ..
-rw-r--r--  1 root root  507990 2008-11-21 13:46 abi-2.6.27-10-generic
-rw-r--r--  1 root root  508385 2008-12-19 17:57 abi-2.6.27-11-generic
-rw-r--r--  1 root root  504442 2008-08-28 18:46 abi-2.6.27-2-generic
-rw-r--r--  1 root root  504882 2008-09-10 17:48 abi-2.6.27-3-generic
-rw-r--r--  1 root root  504774 2008-09-24 03:15 abi-2.6.27-4-generic
-rw-r--r--  1 root root  505136 2008-10-07 05:42 abi-2.6.27-6-generic
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507735 2008-11-06 19:20 abi-2.6.27-8-generic
-rw-r--r--  1 root root   91358 2008-11-21 13:46 config-2.6.27-10-generic
-rw-r--r--  1 root root   91358 2008-12-19 17:57 config-2.6.27-11-generic
-rw-r--r--  1 root root   95861 2008-08-28 18:46 config-2.6.27-2-generic
-rw-r--r--  1 root root   95888 2008-09-10 17:48 config-2.6.27-3-generic
-rw-r--r--  1 root root   95910 2008-09-24 03:15 config-2.6.27-4-generic
-rw-r--r--  1 root root   91299 2008-10-07 05:42 config-2.6.27-6-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-06 19:20 config-2.6.27-8-generic
drwxr-xr-x  2 root root    4096 2008-12-21 17:13 grub
-rw-r--r--  1 root root 8127613 2008-12-03 19:50 initrd.img-2.6.27-10-generic
-rw-r--r--  1 root root 8131145 2008-12-21 17:14 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8127009 2008-09-09 02:37 initrd.img-2.6.27-2-generic
-rw-r--r--  1 root root 8124434 2008-09-19 21:37 initrd.img-2.6.27-3-generic
-rw-r--r--  1 root root 8067857 2008-10-03 19:48 initrd.img-2.6.27-4-generic
-rw-r--r--  1 root root 8114952 2008-10-08 22:23 initrd.img-2.6.27-6-generic
-rw-r--r--  1 root root 8107644 2008-11-05 12:06 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8127464 2008-11-22 05:20 initrd.img-2.6.27-8-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029828 2008-11-21 13:46 System.map-2.6.27-10-generic
-rw-r--r--  1 root root 1031799 2008-12-19 17:57 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1041331 2008-08-28 18:46 System.map-2.6.27-2-generic
-rw-r--r--  1 root root 1042120 2008-09-10 17:48 System.map-2.6.27-3-generic
-rw-r--r--  1 root root 1041452 2008-09-24 03:15 System.map-2.6.27-4-generic
-rw-r--r--  1 root root 1031071 2008-10-07 05:42 System.map-2.6.27-6-generic
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029612 2008-11-06 19:20 System.map-2.6.27-8-generic
-rw-r--r--  1 root root    1074 2008-11-21 13:48 vmcoreinfo-2.6.27-10-generic
-rw-r--r--  1 root root    1074 2008-12-19 17:58 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1073 2008-08-28 18:48 vmcoreinfo-2.6.27-2-generic
-rw-r--r--  1 root root    1073 2008-09-10 17:50 vmcoreinfo-2.6.27-3-generic
-rw-r--r--  1 root root    1073 2008-09-24 03:17 vmcoreinfo-2.6.27-4-generic
-rw-r--r--  1 root root    1073 2008-10-07 05:43 vmcoreinfo-2.6.27-6-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-06 19:22 vmcoreinfo-2.6.27-8-generic
-rw-r--r--  1 root root 2247280 2008-11-21 13:46 vmlinuz-2.6.27-10-generic
-rw-r--r--  1 root root 2248912 2008-12-19 17:57 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2304400 2008-09-06 18:50 vmlinuz-2.6.27-2-generic
-rw-r--r--  1 root root 2305840 2008-09-10 17:48 vmlinuz-2.6.27-3-generic
-rw-r--r--  1 root root 2305072 2008-09-24 03:15 vmlinuz-2.6.27-4-generic
-rw-r--r--  1 root root 2249424 2008-10-07 05:42 vmlinuz-2.6.27-6-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-06 19:20 vmlinuz-2.6.27-8-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-21 17:13 .
drwxr-xr-x 3 root root   4096 2008-12-21 17:14 ..
-rw-r--r-- 1 root root    197 2008-09-06 18:51 default
-rw-r--r-- 1 root root     15 2008-09-06 18:51 device.map
-rw-r--r-- 1 root root   8108 2008-09-06 18:51 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-09-06 18:51 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-09-06 18:51 installed-version
-rw-r--r-- 1 root root   8712 2008-09-06 18:51 jfs_stage1_5
-rw-r--r-- 1 root root   7174 2008-12-21 17:13 menu.lst
-rw-r--r-- 1 root root   6744 2008-12-21 17:13 menu.lst~
-rw-r--r-- 1 root root   7352 2008-09-06 18:51 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-09-06 18:51 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-09-06 18:51 stage1
-rw-r--r-- 1 root root 121500 2008-09-06 18:51 stage2
-rw-r--r-- 1 root root   9556 2008-09-06 18:51 xfs_stage1_5

============================= sda3/grub/menu.lst: =============================

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
# kopt=root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-8-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-8-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/initrd.img-2.6.27-8-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-8-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/initrd.img-2.6.27-8-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-6-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-6-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/initrd.img-2.6.27-6-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-6-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-6-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/initrd.img-2.6.27-6-generic

title		Ubuntu 8.10, kernel 2.6.27-4-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-4-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-4-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-4-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/initrd.img-2.6.27-4-generic

title		Ubuntu 8.10, kernel 2.6.27-3-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-3-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/initrd.img-2.6.27-3-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-3-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-3-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/initrd.img-2.6.27-3-generic

title		Ubuntu 8.10, kernel 2.6.27-2-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-2-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro quiet splash 
initrd		/initrd.img-2.6.27-2-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-2-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-2-generic root=UUID=e233827f-fb63-4847-b116-6c58e06a54b6 ro  single
initrd		/initrd.img-2.6.27-2-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

================================== sda3/grub: ==================================

total 195
drwxr-xr-x 2 root root   1024 2008-12-24 22:41 .
drwxr-xr-x 4 root root   3072 2008-12-24 22:21 ..
-rw-r--r-- 1 root root    197 2008-12-24 22:20 default
-rw-r--r-- 1 root root     15 2008-12-24 22:20 device.map
-rw-r--r-- 1 root root   8108 2008-12-24 22:20 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-24 22:20 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-24 22:20 installed-version
-rw-r--r-- 1 root root   8712 2008-12-24 22:20 jfs_stage1_5
-rw-r--r-- 1 root root   7009 2008-12-24 22:41 menu.lst
-rw-r--r-- 1 root root   7029 2008-12-24 22:33 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-24 22:20 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-24 22:20 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-24 22:20 stage1
-rw-r--r-- 1 root root 121500 2008-12-24 22:20 stage2
-rw-r--r-- 1 root root   9556 2008-12-24 22:20 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by winrowc on 2008-12-27
Never mind I found instructions. Thanks for all your help! I really appreciate it.

---

