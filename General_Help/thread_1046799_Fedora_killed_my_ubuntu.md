---
title: "Fedora killed my ubuntu"
date: 2009-01-21
forum: General Help
---

### Post by Kaneda187 on 2009-01-21
I have a problem with grub, I installed fedora to try it out and it got rid of my option to boot ubuntu, i can still get into the ubuntu partition so i was thinking if i find the grub config file then i could bring it over to fedoras grub config and some how make them all get along....ya think this is possible?

---

### Post by caljohnsmith on 2009-01-21
Yes, if you didn't wipe out your Ubuntu partition, probably all you need to do is add it as an option in your Fedora's Grub menu. But in order to help you do that, I would need more info about your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Fedora desktop, open a terminal and do:
```

su -
bash /home/[COLOR="Blue"]<username>[/COLOR]/Desktop/boot_info_script*.sh
```
And replace username with your user name. That script will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it might take to boot Ubuntu from Fedora's Grub.

---

### Post by Kaneda187 on 2009-01-21
all im getting is no such file directory...

---

### Post by inspriation26 on 2009-01-21
Its quite common this sort of thing. When you installed Fedora it probably gave you an option of remove linux partions and reusing them for Fedora. You may have done this by accident and if you have there is no way to reverse this as far as I know. Try resizing the partion you have and reinstalling Ubuntu if you think this happened.

---

### Post by Kaneda187 on 2009-01-21
no i believe  ubuntu is still ther i can acceses all my data through fedora so i think its still ther.....well I hope?

am where could i find the boot info on the system?

---

### Post by Kaneda187 on 2009-01-21
okay got it here are the results 
```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks at sector 74057852 on 
    boot drive #1 for the stage2 file, but no stage2 files can be found at 
    this location.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda6: _________________________________________________________________________

    File system:       swap

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf /grub

sda8: _________________________________________________________________________

    File system:       LVM2_member

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b6b3b6a

/dev/sda1                 63    2,265,164    2,265,102  83 Linux
/dev/sda2     *  117,242,370  234,436,544  117,194,175   7 HPFS/NTFS
/dev/sda3          2,265,165  117,242,369  114,977,205   5 Extended
/dev/sda5          2,265,228   73,945,227   71,680,000  83 Linux
/dev/sda6        112,455,063  117,242,369    4,787,307  82 Linux swap / Solaris
/dev/sda7         73,947,258   74,348,819      401,562  83 Linux
/dev/sda8         74,348,883  112,454,999   38,106,117  8e Linux LVM

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6e2b8d24-79cd-4052-a14b-197f9862d9a7" TYPE="ext2" 
/dev/sda2: UUID="F69C684F9C680D05" TYPE="ntfs" 
/dev/sda5: UUID="a7919898-ad80-437e-803c-5ee965f34e77" TYPE="ext3" 
/dev/sda6: UUID="391cf85d-a1c2-4b90-9c83-a9961b2a96aa" TYPE="swap" 
/dev/sda7: LABEL="/boot" UUID="9f67539a-e9f0-442c-8219-9ca854789064" TYPE="ext3" 
/dev/sda8: UUID="Qa8hWp-GCxV-jHtW-fNcH-mtMH-BRYr-Xb2wMP" TYPE="lvm2pv" 
/dev/dm-0: LABEL="F10-i686-Live" UUID="533fbc6b-0e1f-414d-92ac-3765c275cc11" TYPE="ext3" 
/dev/dm-1: UUID="fbfe938a-aa3d-4437-81e1-7eadf818a981" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/mapper/VolGroup00-LogVol00 on / type ext3 (rw)
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda7 on /boot type ext3 (rw)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
gvfs-fuse-daemon on /home/kaneda/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kaneda)
/dev/sda1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage /boot/grub/grub_riddle.xpm
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
# kopt=root=UUID=a7919898-ad80-437e-803c-5ee965f34e77 ro

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
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a7919898-ad80-437e-803c-5ee965f34e77 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a7919898-ad80-437e-803c-5ee965f34e77 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a7919898-ad80-437e-803c-5ee965f34e77 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a7919898-ad80-437e-803c-5ee965f34e77 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=a7919898-ad80-437e-803c-5ee965f34e77 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=a7919898-ad80-437e-803c-5ee965f34e77 ro  single
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
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=a7919898-ad80-437e-803c-5ee965f34e77 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=391cf85d-a1c2-4b90-9c83-a9961b2a96aa none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda2 /media/starup ntfs-3g defaults,locale=en_IE.UTF-8 0 0

================================== sda5/boot: ==================================

total 43016
drwxr-xr-x  3 root root    4096 2008-12-16 01:59 .
drwxr-xr-x 21 root root    4096 2008-11-28 02:05 ..
-rw-r--r--  1 root root  422838 2008-10-22 04:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   80062 2008-10-22 04:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-11-28 02:05 grub
-rw-r--r--  1 root root 7867127 2008-10-28 02:19 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7867246 2008-10-16 01:42 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 8475983 2008-11-27 02:06 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8476280 2008-12-16 01:59 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root  905617 2008-10-22 04:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1920760 2008-10-22 04:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda5/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2008-11-28 02:05 .
drwxr-xr-x 3 root root   4096 2008-12-16 01:59 ..
-rw-r--r-- 1 root root    197 2008-06-29 07:40 default
-rw-r--r-- 1 root root     15 2008-06-29 07:40 device.map
-rw-r--r-- 1 root root   8056 2008-06-29 07:40 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-06-29 07:40 fat_stage1_5
-????????? ? ?    ?         ?                ? grub_riddle.xpm
-rw-r--r-- 1 root root     16 2008-06-29 07:40 installed-version
-rw-r--r-- 1 root root   8608 2008-06-29 07:40 jfs_stage1_5
-rw-r--r-- 1 root root   5397 2008-11-28 02:05 menu.lst
-rw-r--r-- 1 root root   4973 2008-11-28 02:05 menu.lst~
-rw-r--r-- 1 root root   7324 2008-06-29 07:40 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-06-29 07:40 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-06-29 07:40 stage1
-rw-r--r-- 1 root root 108356 2008-06-29 07:40 stage2
-rw-r--r-- 1 root root   9276 2008-06-29 07:40 xfs_stage1_5

=================== sda5: Location  of files loaded by Grub: ===================


  11.2GB: boot/grub/menu.lst
  11.2GB: boot/grub/stage2
  11.2GB: boot/initrd.img-2.6.24-21-generic
  11.3GB: boot/initrd.img-2.6.24-21-generic.bak
  11.2GB: boot/initrd.img-2.6.27-7-generic
  11.3GB: boot/initrd.img-2.6.27-9-generic
  11.3GB: boot/vmlinuz-2.6.24-21-generic
  11.3GB: boot/vmlinuz-2.6.27-7-generic
  11.3GB: boot/vmlinuz-2.6.27-9-generic
  11.3GB: initrd.img
  11.2GB: initrd.img.old
  11.3GB: vmlinuz
  11.3GB: vmlinuz.old

============================= sda7/grub/menu.lst: =============================


============================= sda7/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,6)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,6)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.9-159.fc10.i686)
	root (hd0,6)
	kernel /vmlinuz-2.6.27.9-159.fc10.i686 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.27.9-159.fc10.i686.img
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,6)
	kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=533fbc6b-0e1f-414d-92ac-3765c275cc11 rhgb quiet
	initrd /initrd-2.6.27.5-117.fc10.i686.img
title Other
	rootnoverify (hd0,1)
	chainloader +1

================================== sda7/grub: ==================================

total 296
drwxr-xr-x 2 root root   1024 2009-01-22 01:54 .
drwxr-xr-x 5 root root   1024 2009-01-22 01:54 ..
-rw-r--r-- 1 root root     63 2009-01-22 00:13 device.map
-rw-r--r-- 1 root root  11736 2009-01-22 00:13 e2fs_stage1_5
-rw-r--r-- 1 root root  11512 2009-01-22 00:13 fat_stage1_5
-rw-r--r-- 1 root root  10744 2009-01-22 00:13 ffs_stage1_5
-rw------- 1 root root    875 2009-01-22 01:54 grub.conf
-rw-r--r-- 1 root root  10736 2009-01-22 00:13 iso9660_stage1_5
-rw-r--r-- 1 root root  12328 2009-01-22 00:13 jfs_stage1_5
lrwxrwxrwx 1 root root     11 2009-01-22 00:13 menu.lst -> ./grub.conf
-rw-r--r-- 1 root root  10968 2009-01-22 00:13 minix_stage1_5
-rw-r--r-- 1 root root  13360 2009-01-22 00:13 reiserfs_stage1_5
-rw-r--r-- 1 root root  40685 2008-10-24 15:40 splash.xpm.gz
-rw-r--r-- 1 root root    512 2009-01-22 00:13 stage1
-rw-r--r-- 1 root root 111004 2009-01-22 00:13 stage2
-rw-r--r-- 1 root root  11008 2009-01-22 00:13 ufs2_stage1_5
-rw-r--r-- 1 root root  10344 2009-01-22 00:13 vstafs_stage1_5
-rw-r--r-- 1 root root  12984 2009-01-22 00:13 xfs_stage1_5

=================== sda7: Location  of files loaded by Grub: ===================


  37.9GB: grub/grub.conf
  37.9GB: grub/menu.lst
  37.9GB: grub/stage2
  37.8GB: initrd-2.6.27.5-117.fc10.i686.img
  37.8GB: initrd-2.6.27.9-159.fc10.i686.img
  37.8GB: vmlinuz-2.6.27.5-117.fc10.i686
  37.8GB: vmlinuz-2.6.27.9-159.fc10.i686

=============================== StdErr Messages: ===============================

ls: cannot access sda5/boot/grub/grub_riddle.xpm: Input/output error
``` so duz this help? and thank you!

---

### Post by caljohnsmith on 2009-01-21
OK, fortunately it looks like it may not take much effort to boot Ubuntu from Fedora's Grub menu. How about doing:
```
su -
gedit /boot/grub/grub.conf
```
And add the following entry to it:
```
title Ubuntu 8.10
configfile (hd0,4)/boot/grub/menu.lst
```
Reboot, try Ubuntu from your Fedora menu, and let me know how far you get.

---

### Post by Kaneda187 on 2009-01-22
well it worked as far as getting into my ubuntu GRUB menu but then it wouldnt boot i tried a few times and then in recovery mode it gave me an error message
like unable to boot target files system and something about missing /SBIN/INIT

so looks like I screwed it.....:(

---

### Post by caljohnsmith on 2009-01-22
Sorry to hear you couldn't boot into Ubuntu after all. Without more information though, I can't really guess what might be the problem, so can you be more specific about what errors you get when you boot Ubuntu? You might want to consider mounting the Ubuntu partition, backing up your important files, and just reinstalling Ubuntu.

---

### Post by sedawk on 2009-01-22
Try adding this to Fedora's menu.lst file:
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=/dev/sda5 ro  
initrd		/boot/initrd.img-2.6.27-9-generic

(I have a dual boot Ubuntu+Fedora system and what I normally do is
 to add the default entry of Ubuntu to Fedora's menu.lst and vice
 versa. I never use the "UUID" syntax because I had some trouble
 with it in the past, so I the "old" way of giving a device like
 /dev/sda5)

The drawback of this solution is that you have to do some re-editing
as soon as a linux kernel was updated!

---

