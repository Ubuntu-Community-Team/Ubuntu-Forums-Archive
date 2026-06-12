---
title: "Vista + ubuntu 8.10 = Grub &quot;Error 17&quot; HELP?!?"
date: 2009-01-22
forum: General Help
---

### Post by markjs on 2009-01-22
I am at wits end!  I have read a lot about this error and am now too tired and frazzled to continue, but here's the deal; I installed Vista on one hard drive, then ubuntu and Grub, (Grub I think on the Vista drive's MBR?) and all was working fine, then POOF!  ERROR 17!  Danger Will Robinson, ERROR 17!

So I do some reading because it is OK to lose the installs though I would prefer not to, and little seems to apply to my specific issue.  Just so we are clear, I have a Biostar GF8100 MX+ SE motherboard with AMD Dual Core and GeForce 8800 GTS etc, etc, etc....I run four separate SATA drives in  I think it's ACHI mode?  Anyway, best thing I came up with was the "Super Grub CD".  Trouble is the only thing I was able to do with the damn thing is finally get back into Vista by booting the partition direct (Vista is my area of expertise).  Before I did this I had tried to use the Vista installation DVD to fix the startup, but no joy!  With XP it's a simple matter, but when I try Vista's "new improved" automated way, it tells me it doesn't find any problem!!!

So my Vista partition is obviously the most important one, and I am not rebooting this hopefully till I have a solution.  What I want to do though, if it's possible, is to restore Vista to boot off it's drive as if it was the only OS.  Then, I want to install ubuntu as the primary boot drive, with grub on it.  So if either system fails, theoretically the other will not.  I have a pretty good idea of how to do this on two new installs, but what I would like to learn is how to fix my existing installs to be the way I describe.  I am sure it's possible, but clueless as to how as I am a Linux/Grub novice.  Thanks in advance!

---

### Post by caljohnsmith on 2009-01-22
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by markjs on 2009-01-22
I have NO idea what this means, but here it is.....

> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => No boot loader? is installed in the MBR of /dev/sdi

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdi1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x341fd45e

/dev/sda1     *           63  625,137,344  625,137,282   7 HPFS/NTFS

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b6d59

/dev/sdb1                 63  299,724,704  299,724,642  83 Linux
/dev/sdb2        299,724,705  312,496,379   12,771,675   5 Extended
/dev/sdb5        299,724,768  312,496,379   12,771,612  82 Linux swap / Solaris

Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition          Start          End         Size System
/dev/sdc1             40      409,639      409,600 EFI System Partition
/dev/sdc2        409,640  312,237,815  311,828,176 -

Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6e04cf64

/dev/sdd1     *           63  625,137,344  625,137,282   7 HPFS/NTFS

Drive sdi: _____________________________________________________________________

Disk /dev/sdi: 4013 MB, 4013948928 bytes
5 heads, 32 sectors/track, 48998 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

/dev/sdi1     *        8,064    7,839,743    7,831,680   b W95 FAT32

/dev/sdi1 ends after the last cylinder of /dev/sdi
blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="24F4E5E2F4E5B668" LABEL="Vista Business x64" TYPE="ntfs" 
/dev/sdb1: UUID="ef9e241c-2b8d-403d-b298-0dea3b56b146" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="680f710f-c781-4cea-8f32-8ee1c6af22f9" TYPE="swap" 
/dev/sdc1: LABEL="EFI" UUID="826A-0900" TYPE="vfat" 
/dev/sdc2: UUID="CA086931A71A1C7C" LABEL="OSX" TYPE="hfsplus" 
/dev/sdd1: UUID="D284E00E84DFF2C9" LABEL="320GB Storage" TYPE="ntfs" 
/dev/sdi1: LABEL="KINGSTON M2" UUID="10B4-5239" TYPE="vfat" 
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
/dev/sdi1 on /media/KINGSTON M2 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================== sda1/Boot: ==================================

total 528
drwxrwxrwx 1 root root   4096 2009-01-17 16:43 .
drwxrwxrwx 1 root root   8192 2009-01-21 10:02 ..
-rwxrwxrwx 1 root root  24576 2009-01-22 16:53 BCD
-rwxrwxrwx 1 root root  21504 2009-01-22 10:06 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-17 12:43 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-17 12:43 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-17 12:43 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-17 16:43 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-17 16:43 da-DK
drwxrwxrwx 1 root root      0 2009-01-17 16:43 de-DE
drwxrwxrwx 1 root root      0 2009-01-17 16:43 el-GR
drwxrwxrwx 1 root root      0 2009-01-17 16:43 en-US
drwxrwxrwx 1 root root      0 2009-01-17 16:43 es-ES
drwxrwxrwx 1 root root      0 2009-01-17 16:43 fi-FI
drwxrwxrwx 1 root root   4096 2009-01-17 16:43 Fonts
drwxrwxrwx 1 root root      0 2009-01-17 16:43 fr-FR
drwxrwxrwx 1 root root      0 2009-01-17 16:43 hu-HU
drwxrwxrwx 1 root root      0 2009-01-17 16:43 it-IT
drwxrwxrwx 1 root root      0 2009-01-17 16:43 ja-JP
drwxrwxrwx 1 root root      0 2009-01-17 16:43 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:44 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-17 16:43 nb-NO
drwxrwxrwx 1 root root      0 2009-01-17 16:43 nl-NL
drwxrwxrwx 1 root root      0 2009-01-17 16:43 pl-PL
drwxrwxrwx 1 root root      0 2009-01-17 16:43 pt-BR
drwxrwxrwx 1 root root      0 2009-01-17 16:43 pt-PT
drwxrwxrwx 1 root root      0 2009-01-17 16:43 ru-RU
drwxrwxrwx 1 root root      0 2009-01-17 16:43 sv-SE
drwxrwxrwx 1 root root      0 2009-01-17 16:43 tr-TR
drwxrwxrwx 1 root root      0 2009-01-17 16:43 zh-CN
drwxrwxrwx 1 root root      0 2009-01-17 16:43 zh-HK
drwxrwxrwx 1 root root      0 2009-01-17 16:43 zh-TW

=========================== sdb1/boot/grub/menu.lst: ===========================

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
timeout		60

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
# kopt=root=UUID=ef9e241c-2b8d-403d-b298-0dea3b56b146 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ef9e241c-2b8d-403d-b298-0dea3b56b146

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
uuid		ef9e241c-2b8d-403d-b298-0dea3b56b146
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ef9e241c-2b8d-403d-b298-0dea3b56b146 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		ef9e241c-2b8d-403d-b298-0dea3b56b146
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ef9e241c-2b8d-403d-b298-0dea3b56b146 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ef9e241c-2b8d-403d-b298-0dea3b56b146
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ef9e241c-2b8d-403d-b298-0dea3b56b146 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ef9e241c-2b8d-403d-b298-0dea3b56b146
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ef9e241c-2b8d-403d-b298-0dea3b56b146 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ef9e241c-2b8d-403d-b298-0dea3b56b146
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


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=ef9e241c-2b8d-403d-b298-0dea3b56b146 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=680f710f-c781-4cea-8f32-8ee1c6af22f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 25516
drwxr-xr-x  3 root root    4096 2009-01-21 17:27 .
drwxr-xr-x 21 root root    4096 2009-01-21 17:26 ..
-rw-r--r--  1 root root  503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 23:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 20:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 23:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-21 18:10 grub
-rw-r--r--  1 root root 8665206 2009-01-21 17:26 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8664619 2009-01-21 17:27 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 23:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 23:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 20:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 23:30 vmlinuz-2.6.27-9-generic

=============================== sdb1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-21 18:10 .
drwxr-xr-x 3 root root   4096 2009-01-21 17:27 ..
-rw-r--r-- 1 root root    197 2009-01-21 11:21 default
-rw-r--r-- 1 root root     45 2009-01-21 11:21 device.map
-rw-r--r-- 1 root root   8108 2009-01-21 11:21 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-21 11:21 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-21 11:21 installed-version
-rw-r--r-- 1 root root   8712 2009-01-21 11:21 jfs_stage1_5
-rw-r--r-- 1 root root   5101 2009-01-21 18:10 menu.lst
-rw-r--r-- 1 root root   5101 2009-01-21 17:26 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-21 11:21 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-21 11:21 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-21 11:21 stage1
-rw-r--r-- 1 root root 121460 2009-01-21 11:21 stage2
-rw-r--r-- 1 root root   9556 2009-01-21 11:21 xfs_stage1_5

=================== sdb1: Location  of files loaded by Grub: ===================


 138.7GB: boot/grub/menu.lst
 138.6GB: boot/grub/stage2
 138.7GB: boot/initrd.img-2.6.27-7-generic
 138.6GB: boot/initrd.img-2.6.27-9-generic
 138.6GB: boot/vmlinuz-2.6.27-7-generic
 138.6GB: boot/vmlinuz-2.6.27-9-generic
 138.6GB: initrd.img
 138.7GB: initrd.img.old
 138.6GB: vmlinuz
 138.6GB: vmlinuz.old

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 00 09 6a 82 45  46 49 20 20 20 20 20 20  |..)..j.EFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e c0 8e d8 b0 48 e8  |.1............H.|
00000010  3d 01 66 8b 44 20 e8 54  01 66 31 c0 66 a3 00 e4  |=.f.D .T.f1.f...|
00000020  80 7c 03 48 75 03 e9 09  00 be a6 7d e8 10 01 e9  |.|.Hu......}....|
00000030  c2 00 b0 5d e8 18 01 b0  01 31 db 8e c3 bb 00 14  |...].....1......|
00000040  66 b9 02 00 00 00 e8 ae  00 73 03 e9 9b 00 a1 00  |f........s......|
00000050  14 3d 42 44 75 3f b0 7c  e8 f4 00 66 8b 1e 14 14  |.=BDu?.|...f....|
00000060  66 0f cb 66 c1 fb 09 66  31 c0 a1 7e 14 86 c4 52  |f..f...f1..~...R|
00000070  66 f7 e3 5a 66 31 db 8b  1e 1c 14 86 df 66 01 d8  |f..Zf1.......f..|
00000080  66 40 66 40 66 89 c1 b0  01 31 db 8e c3 bb 00 14  |f@f@f....1......|
00000090  e8 64 00 72 54 b0 7d e8  b5 00 a1 00 14 3d 48 2b  |.d.rT.}......=H+|
000000a0  74 05 3d 48 58 75 42 b0  2a e8 a3 00 66 a1 28 14  |t.=HXuB.*...f.(.|
000000b0  66 0f c8 66 c1 f8 09 66  8b 1e c0 15 66 0f cb 52  |f..f...f....f..R|
000000c0  66 f7 e3 5a 66 48 66 48  66 01 c1 b0 21 e8 7f 00  |f..ZfHfHf...!...|
000000d0  b0 7e bb 00 20 8e c3 bb  00 02 e8 1a 00 72 0a b0  |.~.. ........r..|
000000e0  59 e8 6b 00 ea 00 02 00  20 be bd 7d e8 50 00 b0  |Y.k..... ..}.P..|
000000f0  58 e8 5b 00 f4 eb fd 66  60 89 e5 1e 1e 66 03 0e  |X.[....f`....f..|
00000100  00 e4 66 03 4c 20 66 51  06 53 30 e4 50 50 b0 2d  |..f.L fQ.S0.PP.-|
00000110  e8 3c 00 66 89 c8 e8 54  00 b0 3d e8 31 00 58 e8  |.<.f...T..=.1.X.|
00000120  4b 00 68 10 00 89 e6 b4  42 cd 13 73 0d e8 3d 00  |K.h.....B..s..=.|
00000130  b0 52 e8 1a 00 31 c0 cd  13 f9 89 ec 66 61 c3 bb  |.R...1......fa..|
00000140  01 00 fc ac 3c 00 74 06  b4 0e cd 10 eb f5 c3 66  |....<.t........f|
00000150  60 bb 01 00 b4 0e cd 10  66 61 c3 66 60 31 c9 88  |`.......fa.f`1..|
00000160  c1 b0 20 e3 05 e8 e7 ff  e2 f9 66 61 c3 66 60 b9  |.. .......fa.f`.|
00000170  04 00 66 0f c8 50 c0 c8  04 e8 17 00 58 e8 13 00  |..f..P......X...|
00000180  66 c1 c8 08 e2 ef b0 0a  e8 c4 ff b0 0d e8 bf ff  |f...............|
00000190  66 61 c3 24 0f 04 30 3c  39 76 02 04 07 e8 af ff  |fa.$..0<9v......|
000001a0  c3 b4 00 cd 16 c3 0a 0d  48 46 53 2b 20 70 61 72  |........HFS+ par|
000001b0  74 69 74 69 6f 6e 20 65  72 72 6f 72 00 0a 0d 45  |tition error...E|
000001c0  72 72 6f 72 20 6c 6f 61  64 69 6e 67 20 62 6f 6f  |rror loading boo|
000001d0  74 65 72 00 00 00 00 00  00 00 00 00 00 00 00 00  |ter.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

=============================== StdErr Messages: ===============================

sed: can't read sdc2/etc/issue: No such file or directory

---

### Post by caljohnsmith on 2009-01-22
It looks like the reason you are getting a Grub error 17 is because you have Grub installed to the MBR (Master Boot Record) of your Vista drive, and it points to the 2nd drive in the BIOS boot order for its boot files (i.e. what should be the Ubuntu drive). But since you are getting a Grub error 17, that means your Ubuntu drive is not the 2nd boot drive, which could easily be true since you have more than two drives. Can you change your BIOS to boot the Ubuntu sdb drive on start up before the Vista sda drive? If so, that would be the most ideal solution to your problem I think, because all you would need to do is install Grub to your sdb drive to make it bootable; also, if you can boot the Ubuntu drive on start up, you can keep your drives independent of each other as far as booting is concerned, so if anything happens to one of your drives, you should be able to boot into the OS on the other drive. If that sounds good, how about doing:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
Then reboot, set your BIOS to boot the Ubuntu drive, and if all goes well you should be able to boot into Ubuntu. If that works OK, when you get into Ubuntu how about doing:
```
gksudo gedit /boot/grub/menu.lst
```
And replace the Vista entry at the bottom of the file with the following entries:
```
title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Reboot, try booting each Vista entry from the Grub menu, and one of them should work to boot you into Vista; if not, let me know exactly what happens when you try each one and we can work from there. Otherwise let me know how it goes.

---

### Post by markjs on 2009-01-23
Well it's odd because I found out how to fix it easier by accident but I do not know why it happened!

You see I was messing with OSX x86, and somehow it was fine for a while, but then, even with the SATA cables the same, the machine changed which drive was which.  Both drives are identical WD 160GB SATA drives, and I have Identical Seagate 320s with Vista and my backups.  Not sure how it could happen but I discovered it by simply unplugging the OSX drive and then it worked as normal.

---

### Post by markjs on 2009-01-23
PERFECT!

You forgot one thing though!  How do I remove Grub from the Vista drive?  I did it with the Super Grub Disk, although I was nervous because in it's menu it lists 2K, XP, and 2003 but not Vista!  Still I risked it and succeeded, but it would be very nice to know how I could have done it from within ubuntu, and I'd still like to know.

I also wonder is there an option anywhere in the ubuntu install about where to put Grub?  I build and fix PCs for people and I'd like to start selling the more competent ones on ubuntu.  I intend to try and do more and more with it myself, but the average user I work for will still always need a dual boot, so I just wonder how one would set it up so that it would boot off either drive just fine if one unplugged one or the other, because that's the simplest thing to fix if a panic stricken customer should call me.

I usually avoid two OS's on one physical drive because it can be a recipe for disaster, and I like backup plans.  It really irks me about Vista not being able to fix itself though.  Used to be  when I'd screw up my windows drive (XP) with Grub, that it was a simple fix.  It should be with Vista, but I could not have done it without Linux that I know of.

Thanks again man!

---

### Post by caljohnsmith on 2009-01-23
When you go to install Ubuntu, at about the last installation step, just click the "Advanced" button, and there you can specify where Grub is installed to. So in your case, if you are installing Ubuntu to the sdb drive for example, you could specify to have Grub installed to /dev/sdb in order to keep Grub on the same drive. Also, if you ever need to restore a Windows MBR, one way to do it from Ubuntu is:
```
sudo apt-get install lilo
sudo lilo -M /dev/[COLOR="Blue"]sda[/COLOR] mbr
```
And replace sda with the drive you want to install a Windows equivalent MBR to. All Windows versions that I'm aware of (XP, Vista, Win7, etc) use the same boot code in the MBR, so the above technique should work for all versions of Windows (or at least all recent versions, I don't know about really ancient versions like Windows 3.1 or whatever it was called). Glad you have it all sorted out though; cheers and enjoy all your OSes. :)

---

