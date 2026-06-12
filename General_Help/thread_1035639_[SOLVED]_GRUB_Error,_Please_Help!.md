---
title: "[SOLVED] GRUB Error, Please Help!"
date: 2009-01-09
forum: General Help
---

### Post by tdashroy on 2009-01-09
So recently I attempted to install ubuntu onto an external hard drive of mine. In the process I'm pretty sure I messed up my GRUB somehow, because now I am not able to boot into my computer without my external hard drive being plugged in. When I try I get a GRUB Error 21, error message. I have a dual boot setup where I can boot into either windows xp, or ubuntu 8.10. Can someone pleasee help me get it to where I do not have to have my external hard drive plugged in to get my computer to boot. Thx.

-Troy

---

### Post by adult swim on 2009-01-09
you are going to need to reinstall grub to your computers hard drive 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
if you have questions about that post back. youll probably also need to add windows back to your menu.lst file after you have reinstalled grub.  if you have questions about that post back.

---

### Post by caljohnsmith on 2009-01-10
It sounds to me like you have the classic case of having Grub installed to the MBR (Master Boot Record) of your internal drive, while Ubuntu is on your external drive; thus when you disconnect your external drive, Grub gives you an error 21 since it can't access its boot files. Usually the best way to solve that problem is to install Grub to the MBR of your Ubuntu external drive, restore a Windows MBR to your internal drive, set your BIOS to boot the external Ubuntu drive, and then you should be able to boot Ubuntu just fine. Then when you disconnect the external drive and instead boot the internal drive, you will boot directly into Windows (assuming you have Windows on your internal drive). Also, if you do have Windows on your internal drive, I can help you add Windows to your Grub menu if you want so you can conveniently boot Windows from your Ubuntu drive when you want to. If that sounds like what you want, then the first thing to do would be to install Grub to the MBR of the Ubuntu drive by doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
And then to restore a Windows MBR to your Windows drive, you can do:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
Then reboot, set your BIOS to boot the Ubuntu drive, and if all goes well you should be able to boot into Ubuntu (assuming you are using Intrepid, because if you use a previous Ubuntu version, your Grub's menu.lst will most likely need some tweaking). Let me know how that goes or if you run into problems.

---

### Post by tdashroy on 2009-01-11
Okay, thank you both for the replies. caljohnsmith, I did what you said and I no longer have to have my external hard drive plugged in to boot into my computer. 

I now have another question, when I used to boot, I would get the choice of booting into ubuntu (the one on my internal hard drive) or into windows (which is also on my internal hard drive). Then, when I would boot into windows, it would bring me to another screen where I again had the choice of booting into windows or ubuntu, but this screen did not have all the ubuntu choices of different kernels and whatnot, but rather just said "ubuntu". This happened after I installed ubuntu onto my external hard drive. Now currently when I boot, it just goes to the ladder of the two screens and I don't get the options of being able to boot into the different kernels or into the safe mode of ubuntu, but rather just to choose windows xp or "ubuntu", like I said above when I used to select windows xp from the screen with the different kernels.

Any help on how to get my GRUB to show all of the kernels for ubuntu would be greatly appreciated. Thx again.

-Troy

---

### Post by caljohnsmith on 2009-01-11
It sounds like the issue is that you did a Wubi Ubuntu install inside of Windows instead of a standard Ubuntu install to its own partition. So to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup, and we can work from there. :)

---

### Post by tdashroy on 2009-01-11
Alright here are the results.

```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325   195398594    97659135    7  HPFS/NTFS
/dev/sda3       302760990   312496379     4867695   db  CP/M / CTOS / ...
/dev/sda4       195398595   302760989    53681197+   5  Extended
/dev/sda5       195398658   298278854    51440098+  83  Linux
/dev/sda6       298278918   302760989     2241036   82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0C14" TYPE="vfat" 
/dev/sda2: UUID="5E24167024164C01" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sda5: UUID="d1c331e8-b0d5-4587-8474-3471a438b0ba" TYPE="ext3" 
/dev/sda6: UUID="b3b0d97f-8761-4bb8-93b3-d213b015c38d" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/tdashroy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tdashroy)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b3b0d97f-8761-4bb8-93b3-d213b015c38d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda5/boot: ==================================

total 42092
drwxr-xr-x  3 root root    4096 2009-01-11 09:30 .
drwxr-xr-x 21 root root    4096 2008-11-30 21:42 ..
-rw-r--r--  1 root root  422838 2008-10-21 22:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  507665 2008-11-04 15:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 17:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root     512 2009-01-11 09:30 boot.0800
-rw-r--r--  1 root root     512 2008-10-04 00:58 boot.0850
-rw-r--r--  1 root root  308326 2008-10-30 18:14 coffee.bmp
-rw-r--r--  1 root root   80062 2008-10-21 22:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   91364 2008-11-04 15:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 17:46 config-2.6.27-9-generic
lrwxrwxrwx  1 root root      15 2008-10-04 00:57 debian.bmp -> /boot/sarge.bmp
-rw-r--r--  1 root root  153720 2008-10-30 18:14 debianlilo.bmp
drwxr-xr-x  3 root root    4096 2009-01-07 01:57 grub
-rw-r--r--  1 root root 7488202 2008-10-28 11:18 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7488218 2008-10-15 02:50 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 8109452 2008-11-10 21:03 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8128932 2008-12-21 13:22 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root   23662 2008-10-30 18:14 sarge.bmp
-rw-r--r--  1 root root   24116 2008-10-30 18:14 sid.bmp
-rw-r--r--  1 root root  905617 2008-10-21 22:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1029585 2008-11-04 15:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 17:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 15:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 17:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1920760 2008-10-21 22:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 2244464 2008-11-04 15:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 17:46 vmlinuz-2.6.27-9-generic

=============================== sda5/boot/grub: ===============================

total 224
drwxr-xr-x 3 root root   4096 2009-01-07 01:57 .
drwxr-xr-x 3 root root   4096 2009-01-11 09:30 ..
-rw-r--r-- 1 root root    197 2008-10-01 13:45 default
-rw-r--r-- 1 root root     15 2008-10-01 13:45 device.map
-rw-r--r-- 1 root root   8056 2008-10-01 13:45 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-01 13:45 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-01 13:46 installed-version
-rw-r--r-- 1 root root   8608 2008-10-01 13:45 jfs_stage1_5
-rw-r--r-- 1 root root   5528 2008-11-30 21:42 menu.lst
-rw-r--r-- 1 root root   5104 2008-11-30 21:42 menu.lst~
-rw-r--r-- 1 root root   5187 2008-10-25 16:13 menu.lst.backup
-rw-r--r-- 1 root root   7324 2008-10-01 13:45 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-01 13:45 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-10-25 16:13 splashimages
-rw-r--r-- 1 root root    512 2008-10-01 13:45 stage1
-rw-r--r-- 1 root root 108356 2008-10-01 13:46 stage2
-rw-r--r-- 1 root root   9276 2008-10-01 13:45 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda3

00000000  e9 9d 00 44 65 6c 6c 20  38 2e 30 00 02 08 20 00  |...Dell 8.0... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 1e c4 0b 12  |........?.......|
00000020  de 8c 94 00 17 25 00 00  00 00 00 00 02 00 00 00  |.....%..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 00 00 00 00 44  65 6c 6c 52 65 73 74 6f  |..)....DellResto|
00000050  72 65 46 41 54 33 32 20  20 20 10 00 01 00 00 00  |reFAT32   ......|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000080  44 45 4c 4c 42 49 4f 20  42 49 4e 44 69 73 6b 20  |DELLBIO BINDisk |
00000090  65 72 72 6f 72 00 4e 6f  20 6c 6f 61 64 65 72 00  |error.No loader.|
000000a0  33 c0 8e d0 bc 00 07 fc  b9 80 00 8e d8 be 00 7c  |3..............||
000000b0  b8 00 20 8e c0 33 ff f3  66 a5 ea bf 00 00 20 0e  |.. ..3..f..... .|
000000c0  1f 66 a1 1c 00 66 40 66  a3 62 00 c7 06 5e 00 00  |.f...f@f.b...^..|
000000d0  02 c7 06 60 00 00 20 c6  06 5c 00 02 e8 03 00 e9  |...`.. ..\......|
000000e0  22 01 56 b4 42 b0 00 8a  16 40 00 be 5a 00 cd 13  |".V.B....@..Z...|
000000f0  5e 72 05 0a e4 75 01 c3  e9 c2 01 00 00 00 00 00  |^r...u..........|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
```

---

### Post by caljohnsmith on 2009-01-11
The output of the script that you posted only shows your Windows sda drive; did you have your external HDD disconnected? Your Windows directory has "wubildr.mbr" in it, so you definitely did a Wubi install at some point. Yet you also have a Ubuntu 8.10 installed to its own partition on sda5. I would recommend reinstalling Grub to the MBR of your sda drive in order to restore your dual boot between Windows and Ubuntu on that drive; if you do that, it looks like your Grub's menu.lst is all ready configured correctly to boot either Ubuntu or Windows on the sda drive. If that sounds good to you, how about doing:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
And then you should be able to boot either Windows or Ubuntu on your sda drive. Be sure not to choose the "Dell Utility Partition" entry in your Grub menu though, because it looks like that will boot your Windows recovery partition and maybe overwrite Ubuntu by restoring Windows to the HDD (or at least that's what often happens); instead use the "Windows XP Media Center Edition" entry in the Grub menu and you should be fine. Note though when you select to boot Windows from Grub, you will get the Windows boot menu where you can select either Windows or "Ubuntu" which is your Wubi install. If you want help with your Wubi install, then please post the output of the script you ran with your external HDD connected. Let me know how it goes or if you run into problems.

---

### Post by tdashroy on 2009-01-12
Okay, so I did what you said first, and it worked just as you described. So now I have the GRUB screen that lists all the kernels. But now, as you also said would be the case, I have the problem of after selecting windows, it goes to that other screen with just the two choices of windows xp or ubuntu. I would greatly appreciate any help you can offer for this as well.

Here is the the results file with my external hdd connected. I connected it after I booted it, so if I need to have it connected prior to booting up the computer please let me know. And once again, thanks a lot :).

```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda6: _________________________________________________________________________

    File system:       swap

sdf1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdf2: _________________________________________________________________________

    File system:       Extended Partition

sdf5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325   195398594    97659135    7  HPFS/NTFS
/dev/sda3       302760990   312496379     4867695   db  CP/M / CTOS / ...
/dev/sda4       195398595   302760989    53681197+   5  Extended
/dev/sda5       195398658   298278854    51440098+  83  Linux
/dev/sda6       298278918   302760989     2241036   82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x84620b78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   970727624   485363781   83  Linux
/dev/sdf2       970727625   976768064     3020220    5  Extended
/dev/sdf5       970727688   976768064     3020188+  82  Linux swap / Solaris

sfdisk -V /dev/sdf:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdf: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0C14" TYPE="vfat" 
/dev/sda2: UUID="5E24167024164C01" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sda5: UUID="d1c331e8-b0d5-4587-8474-3471a438b0ba" TYPE="ext3" 
/dev/sda6: UUID="b3b0d97f-8761-4bb8-93b3-d213b015c38d" TYPE="swap" 
/dev/sdf1: UUID="ba8332b3-b477-4b21-9a15-65c1a60ada44" TYPE="ext3" 
/dev/sdf5: UUID="a61ce903-eade-421b-b379-4bea6a491f61" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/tdashroy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tdashroy)
/dev/sdf1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b3b0d97f-8761-4bb8-93b3-d213b015c38d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda5/boot: ==================================

total 42092
drwxr-xr-x  3 root root    4096 2009-01-11 09:30 .
drwxr-xr-x 21 root root    4096 2008-11-30 21:42 ..
-rw-r--r--  1 root root  422838 2008-10-21 22:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  507665 2008-11-04 15:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 17:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root     512 2009-01-11 09:30 boot.0800
-rw-r--r--  1 root root     512 2008-10-04 00:58 boot.0850
-rw-r--r--  1 root root  308326 2008-10-30 18:14 coffee.bmp
-rw-r--r--  1 root root   80062 2008-10-21 22:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   91364 2008-11-04 15:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 17:46 config-2.6.27-9-generic
lrwxrwxrwx  1 root root      15 2008-10-04 00:57 debian.bmp -> /boot/sarge.bmp
-rw-r--r--  1 root root  153720 2008-10-30 18:14 debianlilo.bmp
drwxr-xr-x  3 root root    4096 2009-01-07 01:57 grub
-rw-r--r--  1 root root 7488202 2008-10-28 11:18 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7488218 2008-10-15 02:50 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 8109452 2008-11-10 21:03 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8128932 2008-12-21 13:22 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root   23662 2008-10-30 18:14 sarge.bmp
-rw-r--r--  1 root root   24116 2008-10-30 18:14 sid.bmp
-rw-r--r--  1 root root  905617 2008-10-21 22:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1029585 2008-11-04 15:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 17:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 15:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 17:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1920760 2008-10-21 22:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 2244464 2008-11-04 15:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 17:46 vmlinuz-2.6.27-9-generic

=============================== sda5/boot/grub: ===============================

total 224
drwxr-xr-x 3 root root   4096 2009-01-07 01:57 .
drwxr-xr-x 3 root root   4096 2009-01-11 09:30 ..
-rw-r--r-- 1 root root    197 2008-10-01 13:45 default
-rw-r--r-- 1 root root     15 2008-10-01 13:45 device.map
-rw-r--r-- 1 root root   8056 2008-10-01 13:45 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-01 13:45 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-01 13:46 installed-version
-rw-r--r-- 1 root root   8608 2008-10-01 13:45 jfs_stage1_5
-rw-r--r-- 1 root root   5528 2008-11-30 21:42 menu.lst
-rw-r--r-- 1 root root   5104 2008-11-30 21:42 menu.lst~
-rw-r--r-- 1 root root   5187 2008-10-25 16:13 menu.lst.backup
-rw-r--r-- 1 root root   7324 2008-10-01 13:45 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-01 13:45 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-10-25 16:13 splashimages
-rw-r--r-- 1 root root    512 2008-10-01 13:45 stage1
-rw-r--r-- 1 root root 108356 2008-10-01 13:46 stage2
-rw-r--r-- 1 root root   9276 2008-10-01 13:45 xfs_stage1_5

=========================== sdf1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d1c331e8-b0d5-4587-8474-3471a438b0ba ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdf1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdf1
UUID=ba8332b3-b477-4b21-9a15-65c1a60ada44 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdf5
UUID=a61ce903-eade-421b-b379-4bea6a491f61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdf1/boot: ==================================

total 42088
drwxr-xr-x  3 root root    4096 2008-12-21 13:22 .
drwxr-xr-x 20 root root    4096 2009-01-07 01:42 ..
-rw-r--r--  1 root root  422838 2008-10-21 22:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  507665 2008-11-04 15:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 17:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root     512 2008-10-04 00:58 boot.0850
-rw-r--r--  1 root root  308326 2008-10-30 18:14 coffee.bmp
-rw-r--r--  1 root root   80062 2008-10-21 22:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   91364 2008-11-04 15:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 17:46 config-2.6.27-9-generic
lrwxrwxrwx  1 root root      15 2009-01-07 01:30 debian.bmp -> /boot/sarge.bmp
-rw-r--r--  1 root root  153720 2008-10-30 18:14 debianlilo.bmp
drwxr-xr-x  3 root root    4096 2008-11-30 21:42 grub
-rw-r--r--  1 root root 7488202 2008-10-28 11:18 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7488218 2008-10-15 02:50 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 8109452 2008-11-10 21:03 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8128932 2008-12-21 13:22 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root   23662 2008-10-30 18:14 sarge.bmp
-rw-r--r--  1 root root   24116 2008-10-30 18:14 sid.bmp
-rw-r--r--  1 root root  905617 2008-10-21 22:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1029585 2008-11-04 15:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 17:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 15:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 17:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1920760 2008-10-21 22:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 2244464 2008-11-04 15:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 17:46 vmlinuz-2.6.27-9-generic

=============================== sdf1/boot/grub: ===============================

total 224
drwxr-xr-x 3 root root   4096 2008-11-30 21:42 .
drwxr-xr-x 3 root root   4096 2008-12-21 13:22 ..
-rw-r--r-- 1 root root    197 2008-10-01 13:45 default
-rw-r--r-- 1 root root     15 2008-10-01 13:45 device.map
-rw-r--r-- 1 root root   8056 2008-10-01 13:45 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-01 13:45 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-01 13:46 installed-version
-rw-r--r-- 1 root root   8608 2008-10-01 13:45 jfs_stage1_5
-rw-r--r-- 1 root root   5528 2008-11-30 21:42 menu.lst
-rw-r--r-- 1 root root   5104 2008-11-30 21:42 menu.lst~
-rw-r--r-- 1 root root   5187 2008-10-25 16:13 menu.lst.backup
-rw-r--r-- 1 root root   7324 2008-10-01 13:45 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-01 13:45 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-10-25 16:13 splashimages
-rw-r--r-- 1 root root    512 2008-10-01 13:45 stage1
-rw-r--r-- 1 root root 108356 2008-10-01 13:46 stage2
-rw-r--r-- 1 root root   9276 2008-10-01 13:45 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda3

00000000  e9 9d 00 44 65 6c 6c 20  38 2e 30 00 02 08 20 00  |...Dell 8.0... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 1e c4 0b 12  |........?.......|
00000020  de 8c 94 00 17 25 00 00  00 00 00 00 02 00 00 00  |.....%..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 00 00 00 00 44  65 6c 6c 52 65 73 74 6f  |..)....DellResto|
00000050  72 65 46 41 54 33 32 20  20 20 10 00 01 00 00 00  |reFAT32   ......|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000080  44 45 4c 4c 42 49 4f 20  42 49 4e 44 69 73 6b 20  |DELLBIO BINDisk |
00000090  65 72 72 6f 72 00 4e 6f  20 6c 6f 61 64 65 72 00  |error.No loader.|
000000a0  33 c0 8e d0 bc 00 07 fc  b9 80 00 8e d8 be 00 7c  |3..............||
000000b0  b8 00 20 8e c0 33 ff f3  66 a5 ea bf 00 00 20 0e  |.. ..3..f..... .|
000000c0  1f 66 a1 1c 00 66 40 66  a3 62 00 c7 06 5e 00 00  |.f...f@f.b...^..|
000000d0  02 c7 06 60 00 00 20 c6  06 5c 00 02 e8 03 00 e9  |...`.. ..\......|
000000e0  22 01 56 b4 42 b0 00 8a  16 40 00 be 5a 00 cd 13  |".V.B....@..Z...|
000000f0  5e 72 05 0a e4 75 01 c3  e9 c2 01 00 00 00 00 00  |^r...u..........|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
```

---

### Post by caljohnsmith on 2009-01-12
That's really strange that Ubuntu listed your external drive as "sdf", when there is no drives sdb through sdd it looks like. But the good news is that it looks like you did a standard Ubuntu install to the sdf drive, and the main thing that is preventing you from booting it is that Grub is not installed to its MBR. But it also looks like you copied the menu.lst from the sda5 Ubuntu install into your sdf1 Ubuntu install? Fortunately I see you have a "menu.lst.backup" though in your sdf Grub directory, so hopefully that is the original menu.lst. So to get your sdf Ubuntu drive booting OK, how about trying the following:
```
sudo fdisk -lu
```
Using the above output, check which is your external drive, and if it isn't still "sdf", change the "sdf" references in the commands below to the correct drive name:
```
sudo grub
grub> device (hd0) /dev/[COLOR="Blue"]sdf[/COLOR]
grub> root (hd0,0)
grub> makeactive
grub> setup (hd0)
grub> quit
sudo mount /dev/[COLOR="Blue"]sdf1[/COLOR] /mnt
sudo cp /mnt/boot/grub/menu.lst.backup /mnt/boot/grub/menu.lst
```
Please post the output of all the above commands. Also, it doesn't look like you have your Wubi Ubuntu install on any of the partitions any more, so it should be safe to delete that from your Windows boot menu. To do that, try:
```
sudo umount /mnt
sudo mount /sda2 /mnt
sudo rm /mnt/wubildr.mbr
gksudo gedit /mnt/boot.ini
```
That last command should pull up your Windows boot.ini file, and you can delete the last line in it that is highlighted in red below:
```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
[COLOR="Red"]c:\wubildr.mbr="Ubuntu"[/COLOR]

```
Next reboot, set your BIOS to boot the external drive, and if all goes well you should be able to boot into Ubuntu (hopefully the backup menu.lst is correct). If you run into problems though, please rerun the Boot Info Script again and post the results. We can work from there. :)

---

### Post by tdashroy on 2009-01-12
Okay, what you said worked exactly as I had hoped. My GRUB menu is back to normal. Thank you very much! Here is what you asked me to post:

```
Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x84620b78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   970727624   485363781   83  Linux
/dev/sdb2       970727625   976768064     3020220    5  Extended
/dev/sdb5       970727688   976768064     3020188+  82  Linux swap / Solaris
tdashroy@tdashroy-desktop:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
tdashroy@tdashroy-desktop:~$ sudo mount /dev/sdb1 /mnt
tdashroy@tdashroy-desktop:~$ sudo cp /mnt/boot/grub/menu.lst.backup /mnt/boot/grub/menu.lst



grub> device (hd0) /dev/sdb

grub> root (hd0,0)

grub> makeactive

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

An explanation as to why this might have, well more like probably, happened is that I tried to install ubuntu to my external hard drive through windows, because I was having trouble booting from my cd. Then after that I thought that if I were to move ALL of my files from my ubuntu on my internal hard drive to the ubuntu installed on my external hard drive, that I would have my whole computer backed up to something I could boot to. Apparently it doesn't work that way lol. Thank you for all your help and devotion :). It was much appreciated.

---

### Post by caljohnsmith on 2009-01-12
That's great news, glad it all worked OK. Cheers and have fun with Windows and Ubuntu. :)

---

