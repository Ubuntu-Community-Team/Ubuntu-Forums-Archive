---
title: "Error 22 w/ Vista"
date: 2009-01-01
forum: General Help
---

### Post by Hammy2000 on 2009-01-01
When I try to boot vista in the grub loader on my dual boot system i get an Error 22: No partition exists. Ubuntu loads perfectly fine.
Anyone know how to solve this problem?

thanks

---

### Post by caljohnsmith on 2009-01-01
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Vista booting problem might be.

---

### Post by Hammy2000 on 2009-01-01
```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for its boot files.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 17852416.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sdb1: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2893f6d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    17852415     8925184   83  Linux
/dev/sda2   *    17852416   390719919   186433752    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 2 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x93a148c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   372209984   186096960    f  W95 Ext'd (LBA)
/dev/sdb5           16128   370236863   185110368    7  HPFS/NTFS
/dev/sdb6       370250118   372209984      979933+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: partition 5 does not end at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7b96de1f-149b-4e4d-a817-8c35fe97d273" TYPE="ext2" 
/dev/sda2: UUID="92C25E67C25E5019" TYPE="ntfs" 
/dev/sdb5: UUID="A0F81406F813D97C" TYPE="ntfs" 
/dev/sdb6: UUID="040ec0e6-e909-4fe7-9158-b9cb9279976a" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext2 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/thechristmasham/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=thechristmasham)
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

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
# kopt=root=UUID=7b96de1f-149b-4e4d-a817-8c35fe97d273 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7b96de1f-149b-4e4d-a817-8c35fe97d273

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
uuid		7b96de1f-149b-4e4d-a817-8c35fe97d273
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7b96de1f-149b-4e4d-a817-8c35fe97d273 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		7b96de1f-149b-4e4d-a817-8c35fe97d273
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7b96de1f-149b-4e4d-a817-8c35fe97d273 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7b96de1f-149b-4e4d-a817-8c35fe97d273
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7b96de1f-149b-4e4d-a817-8c35fe97d273 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7b96de1f-149b-4e4d-a817-8c35fe97d273
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7b96de1f-149b-4e4d-a817-8c35fe97d273 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7b96de1f-149b-4e4d-a817-8c35fe97d273
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows Vista/Longhorn (loader)
root		(hd1,1)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=7b96de1f-149b-4e4d-a817-8c35fe97d273 / ext2 errors=remount-ro 0 1
# Entry for /dev/sdb6 :
UUID=040ec0e6-e909-4fe7-9158-b9cb9279976a none swap sw 0 0

================================== sda1/boot: ==================================

total 23728
drwxr-xr-x  3 root root    4096 2008-12-26 21:40 .
drwxr-xr-x 20 root root    4096 2008-12-26 21:39 ..
-rw-r--r--  1 root root  507665 2008-11-04 15:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 17:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 15:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 17:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-26 21:39 grub
-rw-r--r--  1 root root 8162921 2008-12-26 21:39 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8163511 2008-12-26 21:40 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 15:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 17:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 15:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 17:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 15:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 17:46 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-26 21:39 .
drwxr-xr-x 3 root root   4096 2008-12-26 21:40 ..
-rw-r--r-- 1 root root    197 2008-12-26 14:23 default
-rw-r--r-- 1 root root     45 2008-12-26 14:23 device.map
-rw-r--r-- 1 root root   8108 2008-12-26 14:23 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-26 14:23 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-26 14:23 installed-version
-rw-r--r-- 1 root root   8712 2008-12-26 14:23 jfs_stage1_5
-rw-r--r-- 1 root root   5124 2008-12-26 21:39 menu.lst
-rw-r--r-- 1 root root   5040 2008-12-26 21:39 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-26 14:23 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-26 14:23 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-26 14:23 stage1
-rw-r--r-- 1 root root 121460 2008-12-26 14:23 stage2
-rw-r--r-- 1 root root   9556 2008-12-26 14:23 xfs_stage1_5

================================== sda2/Boot: ==================================

total 760
drwxrwxrwx 1 root root   4096 2008-04-16 15:26 .
drwxrwxrwx 1 root root   8192 2008-12-27 18:09 ..
-rwxrwxrwx 1 root root  28672 2008-12-26 20:10 BCD
-rwxrwxrwx 1 root root 262144 2008-12-26 20:07 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-04-16 15:26 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-04-16 15:26 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-04-16 15:26 bootstat.dat
drwxrwxrwx 1 root root      0 2008-04-16 15:26 cs-CZ
drwxrwxrwx 1 root root      0 2008-04-16 15:26 da-DK
drwxrwxrwx 1 root root      0 2008-04-16 15:26 de-DE
drwxrwxrwx 1 root root      0 2008-04-16 15:26 el-GR
drwxrwxrwx 1 root root      0 2008-04-16 15:26 en-US
drwxrwxrwx 1 root root      0 2008-04-16 15:26 es-ES
drwxrwxrwx 1 root root      0 2008-04-16 15:26 fi-FI
drwxrwxrwx 1 root root      0 2008-04-16 15:26 Fonts
drwxrwxrwx 1 root root      0 2008-04-16 15:26 fr-FR
drwxrwxrwx 1 root root      0 2008-04-16 15:26 hu-HU
drwxrwxrwx 1 root root      0 2008-04-16 15:26 it-IT
drwxrwxrwx 1 root root      0 2008-04-16 15:26 ja-JP
drwxrwxrwx 1 root root      0 2008-04-16 15:26 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-20 20:23 memtest.exe
drwxrwxrwx 1 root root      0 2008-04-16 15:26 nb-NO
drwxrwxrwx 1 root root      0 2008-04-16 15:26 nl-NL
drwxrwxrwx 1 root root      0 2008-04-16 15:26 pl-PL
drwxrwxrwx 1 root root      0 2008-04-16 15:26 pt-BR
drwxrwxrwx 1 root root      0 2008-04-16 15:26 pt-PT
drwxrwxrwx 1 root root      0 2008-04-16 15:26 ru-RU
drwxrwxrwx 1 root root      0 2008-04-16 15:26 sv-SE
drwxrwxrwx 1 root root      0 2008-04-16 15:26 tr-TR
drwxrwxrwx 1 root root      0 2008-04-16 15:26 zh-CN
drwxrwxrwx 1 root root      0 2008-04-16 15:26 zh-HK
drwxrwxrwx 1 root root      0 2008-04-16 15:26 zh-TW

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-01
OK, how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then change your current Vista entry to:
```
title		Windows Vista
root		(hd0,1)
chainloader	+1

```
Save, reboot, try to boot Vista, and let me know exactly what happens. Hopefully that should be all it takes to boot Vista.

---

### Post by Hammy2000 on 2009-01-02
booted right up, thanks a bunch

---

