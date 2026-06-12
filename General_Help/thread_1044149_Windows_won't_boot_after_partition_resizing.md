---
title: "Windows won't boot after partition resizing"
date: 2009-01-19
forum: General Help
---

### Post by setsanto on 2009-01-19
Hi,

I resized my partitions yesterday, and now windows won't boot.  When I try select it from the bootloader, I am told "The boot selection failed because a required device is inaccessible".  Help please?

~Setsanto

---

### Post by caljohnsmith on 2009-01-19
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by setsanto on 2009-01-19
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda1 
                       and looks at sector 25821263 of the same hard drive 
                       for the stage2 file and on partition #1 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe2d9758c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   104856254    52428096   83  Linux
/dev/sda2   *   104856255   105257879      200812+   7  HPFS/NTFS
/dev/sda3       105257880   476246924   185494522+   7  HPFS/NTFS
/dev/sda4       476246925   488392064     6072570    5  Extended
/dev/sda5       476246988   488392064     6072538+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3f99d495-9665-4d58-b16a-5de9cdffcc26" TYPE="ext3" 
/dev/sda2: UUID="C690BA7390BA6A17" TYPE="ntfs" 
/dev/sda3: UUID="84ACB886ACB873F0" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="7ada7c07-77a7-4686-b736-429ae632e917" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nick)

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
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=3f99d495-9665-4d58-b16a-5de9cdffcc26 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=quiet splash vga=773

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
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3f99d495-9665-4d58-b16a-5de9cdffcc26 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3f99d495-9665-4d58-b16a-5de9cdffcc26 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3f99d495-9665-4d58-b16a-5de9cdffcc26 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3f99d495-9665-4d58-b16a-5de9cdffcc26 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows 7 Beta
rootnoverify (hd0,1)
makeactive
chainloader +1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3f99d495-9665-4d58-b16a-5de9cdffcc26 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7ada7c07-77a7-4686-b736-429ae632e917 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 53964
drwxr-xr-x  3 root root    4096 2009-01-14 16:23 .
drwxr-xr-x 21 root root    4096 2009-01-18 23:17 ..
-rw-r--r--  1 root root  422667 2008-08-21 00:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-11-24 17:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root  422838 2008-11-27 17:13 abi-2.6.24-23-generic
-rw-r--r--  1 root root   80049 2008-08-21 00:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-11-24 17:47 config-2.6.24-22-generic
-rw-r--r--  1 root root   80051 2008-11-27 17:13 config-2.6.24-23-generic
drwxr-xr-x  3 root root    4096 2009-01-11 22:04 grub
-rw-r--r--  1 root root 7495694 2008-12-31 12:23 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7495040 2008-12-30 17:18 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7496925 2008-12-31 12:23 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7495510 2008-12-30 17:18 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root 7497269 2009-01-14 16:23 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7497214 2009-01-11 16:27 initrd.img-2.6.24-23-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  905170 2008-08-21 00:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-11-24 17:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  905633 2008-11-27 17:13 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1921464 2008-08-21 00:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1921176 2008-11-24 17:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1921976 2008-11-27 17:13 vmlinuz-2.6.24-23-generic

=============================== sda1/boot/grub: ===============================

total 232
drwxr-xr-x 3 root root   4096 2009-01-11 22:04 .
drwxr-xr-x 3 root root   4096 2009-01-14 16:23 ..
-rw-r--r-- 1 root root    197 2009-01-11 21:31 default
-rw-r--r-- 1 root root     15 2008-12-30 10:09 device.map
-rw-r--r-- 1 root root   8056 2009-01-11 21:31 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2009-01-11 21:31 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-11 21:31 installed-version
-rw-r--r-- 1 root root   8608 2009-01-11 21:31 jfs_stage1_5
-rw-r--r-- 1 root root   4708 2009-01-11 22:04 menu.lst
-rw-r--r-- 1 root root   4708 2009-01-11 21:18 menu.lst~
-rw-r--r-- 1 root root   4703 2008-12-31 12:20 menu.lst.backup
-rw-r--r-- 1 root root   4703 2008-12-31 12:12 menu.lst.bak1
-rw-r--r-- 1 root root   7324 2009-01-11 21:31 minix_stage1_5
-rw-r--r-- 1 root root   9632 2009-01-11 21:31 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-12-31 12:20 splashimages
-rw-r--r-- 1 root root    512 2009-01-11 21:31 stage1
-rw-r--r-- 1 root root 108356 2009-01-11 21:31 stage2
-rw-r--r-- 1 root root   9276 2009-01-11 21:31 xfs_stage1_5

================================== sda2/Boot: ==================================

total 600
drwxrwxrwx 1 root root   4096 2009-01-09 01:15 .
drwxrwxrwx 1 root root   4096 2009-01-09 01:17 ..
-rwxrwxrwx 1 root root  32768 2009-01-18 22:15 BCD
-rwxrwxrwx 1 root root  29696 2009-01-18 22:06 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-09 01:15 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-09 01:15 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-09 01:15 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-09 01:15 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-09 01:15 da-DK
drwxrwxrwx 1 root root      0 2009-01-09 01:15 de-DE
drwxrwxrwx 1 root root      0 2009-01-09 01:15 el-GR
drwxrwxrwx 1 root root      0 2009-01-09 01:15 en-US
drwxrwxrwx 1 root root      0 2009-01-09 01:15 es-ES
drwxrwxrwx 1 root root      0 2009-01-09 01:15 fi-FI
drwxrwxrwx 1 root root      0 2009-01-09 01:15 Fonts
drwxrwxrwx 1 root root      0 2009-01-09 01:15 fr-FR
drwxrwxrwx 1 root root      0 2009-01-09 01:15 hu-HU
drwxrwxrwx 1 root root      0 2009-01-09 01:15 it-IT
drwxrwxrwx 1 root root      0 2009-01-09 01:15 ja-JP
drwxrwxrwx 1 root root      0 2009-01-09 01:15 ko-KR
-rwxrwxrwx 1 root root 473864 2008-12-13 02:01 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-09 01:15 nb-NO
drwxrwxrwx 1 root root      0 2009-01-09 01:15 nl-NL
drwxrwxrwx 1 root root      0 2009-01-09 01:15 pl-PL
drwxrwxrwx 1 root root      0 2009-01-09 01:15 pt-BR
drwxrwxrwx 1 root root      0 2009-01-09 01:15 pt-PT
drwxrwxrwx 1 root root      0 2009-01-09 01:15 ru-RU
drwxrwxrwx 1 root root      0 2009-01-09 01:15 sv-SE
drwxrwxrwx 1 root root      0 2009-01-09 01:15 tr-TR
drwxrwxrwx 1 root root      0 2009-01-09 01:15 zh-CN
drwxrwxrwx 1 root root      0 2009-01-09 01:15 zh-HK
drwxrwxrwx 1 root root      0 2009-01-09 01:15 zh-TW

=============================== StdErr Messages: ===============================

No errors were reported.
```

I'm assuming you guys are better at understanding that then me :P.

~Setsanto

---

### Post by caljohnsmith on 2009-01-19
How about booting your Windows 7 Install CD, go to the command line, and do:
```
bootrec /rebuildbcd
```
Next do:
```
diskpart
```
And at the diskpart prompt:
```
list volume
exit
```
Find the drive letters for your sda2 and sda3 NTFS partitions using the above commands, and then do:
```
chkdsk /r C:
```
And replace C with each of the drive letters for the two partitions. Also, run the chkdsk command on each partition as many times as it takes until it reports no errors. Then reboot, and let me know what happens when you try to boot Windows 7 from Grub.

---

### Post by hyperdude111 on 2009-01-19
Windows 7 is a dumdum when it comes to partitioning.
It you re-size the partition after installation it will refuse to boot! The system is fine as all the files are accessible and they are all fine yet 7 wont boot. As is often the case with windows i foun a fresh install the only fix.

---

