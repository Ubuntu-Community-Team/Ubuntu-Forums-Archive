---
title: "Pendrive Install Grub 17"
date: 2008-12-28
forum: General Help
---

### Post by Sam442 on 2008-12-28
Howdy,

I recently setup an ubuntu install on a pen drive, after numerous failures with the "create a usb startup disc" method I tried a regular install from livecd and it worked perfectly, until I ran update, now when I try to boot I get Grub Error 17 (and occasionally Grub Error 2).

Any help would be greatly appreciated.

**sudo fdisk -l**
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003677d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78148608    7  HPFS/NTFS

Disk /dev/sdb: 8006 MB, 8006926336 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003f86c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         391     3140676    c  W95 FAT32 (LBA)
/dev/sdb2             392         973     4674915    5  Extended
/dev/sdb5   *         392         902     4104576   83  Linux
/dev/sdb6             903         973      570276   82  Linux swap / Solaris

```

*sda* is laptop drive with separate mbr.

*sdb1* is a fat32 partition for my data files so I can access them from any pc, ub is installed on *sdb2* which also has the mbr and boot flag


**/media/Ubuntu/boot/grub/menu.lst**
```
## ## End Default Options ##
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		8eb07306-993a-4a4f-bb41-8e66f78e132c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8eb07306-993a-4a4f-bb41-8e66f78e132c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		8eb07306-993a-4a4f-bb41-8e66f78e132c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8eb07306-993a-4a4f-bb41-8e66f78e132c ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8eb07306-993a-4a4f-bb41-8e66f78e132c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8eb07306-993a-4a4f-bb41-8e66f78e132c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8eb07306-993a-4a4f-bb41-8e66f78e132c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8eb07306-993a-4a4f-bb41-8e66f78e132c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8eb07306-993a-4a4f-bb41-8e66f78e132c
kernel		/boot/memtest86+.bin
quiet
```

It was all working fine untill I updated :(

Any ideas?
Thanks.

---

### Post by Sam442 on 2008-12-29
Bumpity :(

---

### Post by Coder543 on 2008-12-29
Grub could be kind of nasty.... note to others who wish to do this in the future. When you get to the ending confirmation dialog on installing to an external drive click advanced and uncheck grub. It to me seems to be the safest thing. Just for the sake of sanity I would recommend reinstalling ubuntu onto the main computer. If that isn't an idea you want to handle, you could google around for reinstalling grub.

---

### Post by caljohnsmith on 2008-12-29
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Grub problem might be.

---

### Post by Sam442 on 2008-12-29
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed to the boot sector of /dev/sdb5 and 
                       looks at sector 10889222 of the same hard drive for 
                       the stage2 file (a stage2 file is at this location on 
                       /dev/sdb) and on partition #5 for menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x88a58df2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31471334    15735636    7  HPFS/NTFS
/dev/sda2        31471335   117210239    42869452+   f  W95 Ext'd (LBA)
/dev/sda5        31471398   117210239    42869421    7  HPFS/NTFS

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 8006 MB, 8006926336 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15638528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003f86c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     6281414     3140676    c  W95 FAT32 (LBA)
/dev/sdb2         6281415    15631244     4674915    5  Extended
/dev/sdb5   *     6281478    14490629     4104576   83  Linux
/dev/sdb6        14490693    15631244      570276   82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: usually one can boot from primary partitions only
LILO disregards the `bootable' flag.
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="115BCB1A03A163C9" LABEL="System" TYPE="ntfs" 
/dev/sda5: UUID="BA5403FC5403BA61" LABEL="Data" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="FLASH" UUID="4957-D024" TYPE="vfat" 
/dev/sdb5: LABEL="Ubuntu" UUID="8eb07306-993a-4a4f-bb41-8e66f78e132c" TYPE="ext3" 
/dev/sdb6: UUID="0979f40f-63ce-4a8a-9ffe-666226cdbbbb" TYPE="swap" 

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
/dev/sdb5 on /media/Ubuntu type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/FLASH type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect




=========================== sdb5/boot/grub/menu.lst: ===========================

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
# root		(hd0,0)
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
# kopt=root=UUID=8eb07306-993a-4a4f-bb41-8e66f78e132c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8eb07306-993a-4a4f-bb41-8e66f78e132c

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
uuid		8eb07306-993a-4a4f-bb41-8e66f78e132c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8eb07306-993a-4a4f-bb41-8e66f78e132c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		8eb07306-993a-4a4f-bb41-8e66f78e132c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8eb07306-993a-4a4f-bb41-8e66f78e132c ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8eb07306-993a-4a4f-bb41-8e66f78e132c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8eb07306-993a-4a4f-bb41-8e66f78e132c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8eb07306-993a-4a4f-bb41-8e66f78e132c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8eb07306-993a-4a4f-bb41-8e66f78e132c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8eb07306-993a-4a4f-bb41-8e66f78e132c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=8eb07306-993a-4a4f-bb41-8e66f78e132c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=0979f40f-63ce-4a8a-9ffe-666226cdbbbb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb5/boot: ==================================

total 23764
drwxr-xr-x  3 root root    4096 2008-12-28 23:21 .
drwxr-xr-x 20 root root    4096 2008-12-28 23:17 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-29 02:23 grub
-rw-r--r--  1 root root 8180827 2008-12-28 23:16 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8180755 2008-12-28 23:21 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sdb5/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-29 02:23 .
drwxr-xr-x 3 root root   4096 2008-12-28 23:21 ..
-rw-r--r-- 1 root root    197 2008-12-28 21:28 default
-rw-r--r-- 1 root root     30 2008-12-28 21:28 device.map
-rw-r--r-- 1 root root   8108 2008-12-28 21:28 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-28 21:28 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-28 21:28 installed-version
-rw-r--r-- 1 root root   8712 2008-12-28 21:28 jfs_stage1_5
-rw-r--r-- 1 root root   4931 2008-12-29 02:23 menu.lst
-rw-r--r-- 1 root root   4917 2008-12-29 02:12 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-28 21:28 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-28 21:28 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-28 21:28 stage1
-rw-r--r-- 1 root root 121460 2008-12-28 21:28 stage2
-rw-r--r-- 1 root root   9556 2008-12-28 21:28 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

(on a different laptop so the hard drive will be different)

<edit>
```
Warning: usually one can boot from primary partitions only
LILO disregards the `bootable' flag.
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK
```
would that be why? having the fat partition first was the only way I could get windows to read it.

---

### Post by caljohnsmith on 2008-12-29
So do you get the Grub error 17 or error 2 before seeing the Grub menu I would think? According to the script results you posted, Grub appears to be configured just fine on your USB stick. If you are getting those type of Grub errors before seeing a Grub menu, that can be a problem with how the drive is set up in BIOS. Can you go into your BIOS and check which settings you have related to USB? I would start there. Also, depending on how old your BIOS is, you might want to consider upgrading it. Good luck and let me know how it goes.

EDIT: Also to avoid problems with your BIOS, it would be good to mark a primary partition bootable on your USB stick, rather than the logical sdb5 partition which is marked bootable right now. To set the boot flag on sdb1 while unsetting the boot flag on sdb5, you can simply do:
```
sudo sfdisk -A1 /dev/sdb
```

---

### Post by Sam442 on 2008-12-29
Yep it's before the grub menu, I don't have access to bios (password that I don't have) so can only boot via f12, trying to setup said pen drive so I can have ubuntu with my personal files on what ever pc I'm using when traveling about.

Seems strange that it worked fine until I updated :(

---

### Post by Sam442 on 2008-12-29
> **caljohnsmith said:**
> 
```
sudo sfdisk -A1 /dev/sdb
```

FIXED IT :D

Don't know why, but it did :D

Thanks for your help.

---

### Post by caljohnsmith on 2008-12-29
> **Sam442 said:**
> FIXED IT :D

Don't know why, but it did :D

Thanks for your help.

I'm glad that seemed to do the trick, but I must admit that I'm a little dubious about whether you might still run into Grub problems in the future with your USB stick. Hopefully not though; cheers and have fun with your Ubuntu install. :)

---

