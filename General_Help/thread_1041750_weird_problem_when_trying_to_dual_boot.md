---
title: "weird problem when trying to dual boot"
date: 2009-01-16
forum: General Help
---

### Post by slade on 2009-01-16
I've had a dual boot system set up for some time with XP/fedora.  I just added ubuntu, and of course grub was overwritten.  here's my partition layout:

/dev/sda1  XP
/dev/sda2  Fedora 10
/dev/sda3  extended partition
/dev/sda5  swap
/dev/sda6  Fedora 8
/dev/sda7  share
/dev/sda8  Ubuntu 8.10

but, inside menu.lst ubuntu automatically set up /dev/sda1 AND /dev/sda6 to boot fedora 8.  everything else is right, except XP is not listed.  I tried adding the following lines to grub:

title       XP
rootnoverify (hd0,0)
chainloader +1

and

title       XP
root        (hd0,0)
makeactive
chainloader +1


but neither of them will boot XP.  they both stall out with 1 test output line, along the lines of "booting OS..."

does anyone have any idea what's going on?

---

### Post by caljohnsmith on 2009-01-16
In order to get a better idea of what the problem might be, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by slade on 2009-01-16
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000400
    Boot sector info:  Geometry: 240 Heads and 63 sectors per Track. 
                       According to the info in the boot sector, sda1 starts 
                       at sector 95249448. But according to the info from 
                       fdisk, sda1 starts at sector 63. According to the info 
                       in the boot sector, sda1 has 51166952 sectors, but 
                       according to the info from fdisk, it has 62508852 
                       sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 10 (Cambridge) Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab 
                       /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 8 (Werewolf) Kernel on an
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab 
                       /boot /boot/grub

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  Geometry: 240 Heads and 63 sectors per Track. No 
                       errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab 
                       /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007f0ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62508914    31254426    7  HPFS/NTFS
/dev/sda2        62508915    87265079    12378082+  83  Linux
/dev/sda3        87265080   556845029   234789975    5  Extended
/dev/sda5        87265143    91458044     2096451   82  Linux swap / Solaris
/dev/sda6        91458108   113868719    11205306   83  Linux
/dev/sda7       113868783   532088864   209110041   83  Linux
/dev/sda8       532088928   556845029    12378051   83  Linux

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006b394

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2              63   976768064   488384001    5  Extended
/dev/sdc5       207077913   917552474   355237281   83  Linux
/dev/sdc6             189    95249384    47624598   83  Linux
/dev/sdc7        95249448   146416409    25583481    7  HPFS/NTFS
/dev/sdc8       146416473   176233049    14908288+  83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sdc:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 5 does not start at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F6149ECE149E90EB" TYPE="ntfs" 
/dev/sda2: LABEL="F10" UUID="c460b2f0-736e-4054-a6d5-4460023a34aa" TYPE="ext3" 
/dev/sda5: UUID="42dd3d1d-6f42-04a3-aea9-956e638b3ccb" TYPE="swap" 
/dev/sda6: LABEL="/1" UUID="b822888a-bb1c-42cb-ab9d-cca3f01a4f55" TYPE="ext3" 
/dev/sda7: LABEL="SHARE" UUID="84ef4e00-0d43-42fb-b123-9b1f97019df1" TYPE="ext3" 
/dev/sda8: UUID="f21c98d3-2d4f-4513-9c7f-77c951a745dc" TYPE="ext3" 
/dev/sdc5: UUID="bd5908b4-ac1b-4ee4-9035-64458fa9c7bf" TYPE="ext3" 
/dev/sdc6: LABEL="SHARE" UUID="84ef4e00-0d43-42fb-b123-9b1f97019df1" TYPE="ext3" 
/dev/sdc7: UUID="F6149ECE149E90EB" TYPE="ntfs" 
/dev/sdc8: LABEL="SABAYON" UUID="87df631c-0aed-4a30-b4d1-a10b98232dbc" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda2 on /mnt/F10 type ext3 (rw,relatime)
/dev/sda6 on /mnt/F8 type ext3 (rw,relatime)
/dev/sda1 on /mnt/XP type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7 on /share type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/colin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=colin)
/dev/sdc7 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc8 on /media/SABAYON type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdc5 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdc6 on /media/SHARE type ext3 (rw,nosuid,nodev,uhelper=hal)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================


========================== sda2/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,1)
#          kernel /boot/vmlinuz-version ro root=/dev/sda2
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.9-159.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.9-159.fc10.i686 ro root=UUID=c460b2f0-736e-4054-a6d5-4460023a34aa rhgb quiet
	initrd /boot/initrd-2.6.27.9-159.fc10.i686.img
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=c460b2f0-736e-4054-a6d5-4460023a34aa rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.i686.img
title Other
	rootnoverify (hd0,0)
	chainloader +1

=============================== sda2/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Fri Jan  2 00:44:29 2009
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or vol_id(8) for more info
#
UUID=c460b2f0-736e-4054-a6d5-4460023a34aa /                       ext3    defaults        1 1
UUID=84ef4e00-0d43-42fb-b123-9b1f97019df1 /share                  ext3    defaults        1 2
UUID=b822888a-bb1c-42cb-ab9d-cca3f01a4f55 /mnt/F8                 ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
LABEL=SWAP-sda5         swap                    swap    defaults        0 0

================================== sda2/boot: ==================================

total 13600
drwxr-xr-x  4 root root    4096 2009-01-01 14:27 .
drwxr-xr-x 23 root root    4096 2009-01-12 23:14 ..
-rw-r--r--  1 root root   90889 2008-11-18 09:30 config-2.6.27.5-117.fc10.i686
-rw-r--r--  1 root root   91102 2008-12-16 12:21 config-2.6.27.9-159.fc10.i686
drwxr-xr-x  3 root root    4096 2009-01-01 16:50 efi
drwxr-xr-x  2 root root    4096 2009-01-01 14:27 grub
-rw-------  1 root root 3161183 2009-01-01 16:52 initrd-2.6.27.5-117.fc10.i686.img
-rw-------  1 root root 3182706 2009-01-01 14:27 initrd-2.6.27.9-159.fc10.i686.img
-rw-r--r--  1 root root 1089949 2008-11-18 09:30 System.map-2.6.27.5-117.fc10.i686
-rw-r--r--  1 root root 1090858 2008-12-16 12:21 System.map-2.6.27.9-159.fc10.i686
-rwxr-xr-x  1 root root 2570960 2008-11-18 09:30 vmlinuz-2.6.27.5-117.fc10.i686
-rwxr-xr-x  1 root root 2575088 2008-12-16 12:21 vmlinuz-2.6.27.9-159.fc10.i686

=============================== sda2/boot/grub: ===============================

total 308
drwxr-xr-x 2 root root   4096 2009-01-01 14:27 .
drwxr-xr-x 4 root root   4096 2009-01-01 14:27 ..
-rw-r--r-- 1 root root     63 2009-01-01 17:00 device.map
-rw-r--r-- 1 root root  11736 2009-01-01 17:00 e2fs_stage1_5
-rw-r--r-- 1 root root  11512 2009-01-01 17:00 fat_stage1_5
-rw-r--r-- 1 root root  10744 2009-01-01 17:00 ffs_stage1_5
-rw------- 1 root root    914 2009-01-01 14:27 grub.conf
-rw-r--r-- 1 root root  10736 2009-01-01 17:00 iso9660_stage1_5
-rw-r--r-- 1 root root  12328 2009-01-01 17:00 jfs_stage1_5
lrwxrwxrwx 1 root root     11 2009-01-01 17:00 menu.lst -> ./grub.conf
-rw-r--r-- 1 root root  10968 2009-01-01 17:00 minix_stage1_5
-rw-r--r-- 1 root root  13360 2009-01-01 17:00 reiserfs_stage1_5
-rw-r--r-- 1 root root  40685 2008-10-24 07:40 splash.xpm.gz
-rw-r--r-- 1 root root    512 2009-01-01 17:00 stage1
-rw-r--r-- 1 root root 111004 2009-01-01 17:00 stage2
-rw-r--r-- 1 root root  11008 2009-01-01 17:00 ufs2_stage1_5
-rw-r--r-- 1 root root  10344 2009-01-01 17:00 vstafs_stage1_5
-rw-r--r-- 1 root root  12984 2009-01-01 17:00 xfs_stage1_5

=========================== sda6/boot/grub/menu.lst: ===========================


========================== sda6/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,1)
#          kernel /boot/vmlinuz-version ro root=/dev/sda8
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,5)/boot/grub/splash.xpm.gz
hiddenmenu

title Fedora (2.6.27.7-134.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.7-134.fc10.i686 ro root=/dev/sda2 rhgb quiet
	initrd /boot/initrd-2.6.27.7-134.fc10.i686.img


title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.i686 ro root=/dev/sda2 rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.i686.img


title Fedora (2.6.26.6-49.fc8)
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.26.6-49.fc8 ro root=LABEL=/1 rhgb quiet
	initrd /boot/initrd-2.6.26.6-49.fc8.img
title Fedora (2.6.25.14-69.fc8)
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.25.14-69.fc8 ro root=LABEL=/1 rhgb quiet
	initrd /boot/initrd-2.6.25.14-69.fc8.img


title XP
	rootnoverify (hd0,0)
	chainloader +1

=============================== sda6/etc/fstab: ===============================

/dev/sda6               /                       ext3    defaults        1 1
/dev/sda2               /mnt/F10                ext3    defaults        1 2
/dev/sda7               /share                  ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sda5               swap                    swap    defaults        0 0

================================== sda6/boot: ==================================

total 12180
drwxr-xr-x  3 root root    4096 2008-10-24 02:52 .
drwxr-xr-x 24 root root    4096 2009-01-01 16:36 ..
-rw-r--r--  1 root root   85851 2008-08-04 11:28 config-2.6.25.14-69.fc8
-rw-r--r--  1 root root   88385 2008-10-17 13:10 config-2.6.26.6-49.fc8
drwxr-xr-x  2 root root    4096 2008-12-26 00:36 grub
-rw-------  1 root root 3059568 2008-08-26 18:08 initrd-2.6.25.14-69.fc8.img
-rw-------  1 root root 3059984 2008-10-24 02:51 initrd-2.6.26.6-49.fc8.img
-rw-r--r--  1 root root  909719 2008-08-04 11:28 System.map-2.6.25.14-69.fc8
-rw-r--r--  1 root root  934839 2008-10-17 13:10 System.map-2.6.26.6-49.fc8
-rw-r--r--  1 root root 2095840 2008-08-04 11:28 vmlinuz-2.6.25.14-69.fc8
-rw-r--r--  1 root root 2133568 2008-10-17 13:10 vmlinuz-2.6.26.6-49.fc8

=============================== sda6/boot/grub: ===============================

total 312
drwxr-xr-x 2 root root   4096 2008-12-26 00:36 .
drwxr-xr-x 3 root root   4096 2008-10-24 02:52 ..
-rw-r--r-- 1 root root     63 2008-06-21 14:33 device.map
-rw-r--r-- 1 root root   8096 2008-06-21 14:33 e2fs_stage1_5
-rw-r--r-- 1 root root   7936 2008-06-21 14:33 fat_stage1_5
-rw-r--r-- 1 root root   7200 2008-06-21 14:33 ffs_stage1_5
-rw------- 1 root root   1173 2008-12-26 00:36 grub.conf
-rw------- 1 root root   1237 2008-12-25 21:06 grub.conf~
-rw------- 1 root root   1572 2008-11-05 15:28 grub.conf.bak
-rw-r--r-- 1 root root   7200 2008-06-21 14:33 iso9660_stage1_5
-rw-r--r-- 1 root root   8672 2008-06-21 14:33 jfs_stage1_5
lrwxrwxrwx 1 root root     11 2008-06-21 14:33 menu.lst -> ./grub.conf
-rw-r--r-- 1 root root   7328 2008-06-21 14:33 minix_stage1_5
-rw-r--r-- 1 root root   9696 2008-06-21 14:33 reiserfs_stage1_5
-rw-r--r-- 1 root root   7459 2007-11-14 07:00 splash.xpm.gz
-rw-r--r-- 1 root root    512 2008-06-21 14:33 stage1
-rw-r--r-- 1 root root 105468 2008-06-21 14:33 stage2
-rw-r--r-- 1 root root   7520 2008-06-21 14:33 ufs2_stage1_5
-rw-r--r-- 1 root root   6752 2008-06-21 14:33 vstafs_stage1_5
-rw-r--r-- 1 root root   9344 2008-06-21 14:33 xfs_stage1_5

=========================== sda8/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f21c98d3-2d4f-4513-9c7f-77c951a745dc

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
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Fedora (2.6.26.6-49.fc8) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26.6-49.fc8 ro root=LABEL=/1 rhgb quiet 
initrd		/boot/initrd-2.6.26.6-49.fc8.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Fedora (2.6.25.14-69.fc8) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.25.14-69.fc8 ro root=LABEL=/1 rhgb quiet 
initrd		/boot/initrd-2.6.25.14-69.fc8.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Fedora (2.6.27.9-159.fc10.i686) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27.9-159.fc10.i686 ro root=UUID=c460b2f0-736e-4054-a6d5-4460023a34aa rhgb quiet 
initrd		/boot/initrd-2.6.27.9-159.fc10.i686.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Fedora (2.6.26.6-49.fc8) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.26.6-49.fc8 ro root=LABEL=/1 rhgb quiet 
initrd		/boot/initrd-2.6.26.6-49.fc8.img
savedefault
boot


title		XP
rootnoverify (hd0,0)
chainloader +1

title		XP
root		(hd0,0)
makeactive
chainloader	+1

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>      <options>                  <dump>  <pass>
proc            /proc           proc        defaults                   0       0
/dev/sda8       /               ext3        relatime,errors=remount-ro 0       1
/dev/sda2       /mnt/F10        ext3        relatime                   0       2
/dev/sda6       /mnt/F8         ext3        relatime                   0       2
/dev/sda1       /mnt/XP         ntfs        defaults,umask=007,gid=46  0       1
/dev/sda7       /share          ext3        relatime                   0       2
/dev/sda5       none            swap        sw                         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8      0       0

================================== sda8/boot: ==================================

total 23804
drwxr-xr-x  3 root root    4096 2009-01-13 03:13 .
drwxr-xr-x 21 root root    4096 2009-01-13 03:13 ..
-rw-r--r--  1 root root  507665 2008-11-04 13:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 15:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 13:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 15:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-13 03:13 grub
-rw-r--r--  1 root root 8203368 2009-01-13 03:12 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8202544 2009-01-13 03:13 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 13:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 13:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 15:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 13:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 15:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 13:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 15:46 vmlinuz-2.6.27-9-generic

=============================== sda8/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-13 03:13 .
drwxr-xr-x 3 root root   4096 2009-01-13 03:13 ..
-rw-r--r-- 1 root root    197 2009-01-13 02:46 default
-rw-r--r-- 1 root root     15 2009-01-13 02:46 device.map
-rw-r--r-- 1 root root   8108 2009-01-13 02:46 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-13 02:46 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-13 02:46 installed-version
-rw-r--r-- 1 root root   8712 2009-01-13 02:46 jfs_stage1_5
-rw-r--r-- 1 root root   6280 2009-01-16 18:33 menu.lst
-rw-r--r-- 1 root root   6723 2009-01-13 03:13 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-13 02:46 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-13 02:46 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-13 02:46 stage1
-rw-r--r-- 1 root root 121460 2009-01-13 02:46 stage2
-rw-r--r-- 1 root root   9556 2009-01-13 02:46 xfs_stage1_5

================================ sdc7/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdc8/boot/grub/menu.lst: ===========================


========================== sdc8/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,1)
#          kernel /boot/kernel-genkernel real_root=UUID=87df631c-0aed-4a30-b4d1-a10b98232dbc
#          initrd /boot/initramfs-genkernel
#boot=sda
default=1
#timeout=6
splashimage=(hd0,2)/boot/grub/splash.xpm.gz

title Sabayon Linux x86 3.4
	root (hd0,1)
	kernel /boot/kernel-genkernel-x86-2.6.22-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=87df631c-0aed-4a30-b4d1-a10b98232dbc  quiet  init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 pci=nomsi 
	initrd /boot/initramfs-genkernel-x86-2.6.22-sabayon

title fedora 9 2.6.25-14
	root (hd0,7)
	kernel /boot/vmlinuz-2.6.25-14.fc9.i686 ro root=/dev/sda8 quiet
	initrd /boot/initrd-2.6.25-14.fc9.i686.img

title fedora 8 *85
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.24.5-85.fc8 ro root=/dev/sda7 quiet
	initrd /boot/initrd-2.6.24.5-85.fc8.img
title fedora 8 *64
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.24.4-64.fc8 ro root=/dev/sda7 quiet
	initrd /boot/initrd-2.6.24.4-64.fc8.img

title XP
	rootnoverify (hd0,0)
	chainloader +1

=============================== sdc8/etc/fstab: ===============================

/dev/disk/by-uuid/87df631c-0aed-4a30-b4d1-a10b98232dbc /                       ext3    user_xattr      1 1
/dev/sda6                                              /share                  ext3    user_xattr      1 2
/dev/sda2                                              /mnt/vista              ntfs    defaults        0 0
/dev/shm                                               /dev/shm                tmpfs   defaults        0 0
/dev/sda5                                              swap                    swap    defaults        0 0
#/dev/sda7                                              /mnt/f7_32              ext3    defaults        1 2
#/dev/sda8                                              /mnt/f7_64              ext3    defaults        1 2
#
#/dev/disk/by-uuid/9187fc26-218b-4a87-8c75-5413275a4f59 /share                  ext3    user_xattr      1 2
#/dev/disk/by-uuid/88aec343-3002-419d-ab9f-c0fd6732be41 swap                    swap    defaults        0 0
#/dev/disk/by-uuid/F856F07F56F03FC4                     /mnt/vista              ntfs    defaults        0 0

================================== sdc8/boot: ==================================

total 9772
drwxr-xr-x  3 root root    4096 2007-08-29 13:19 .
drwxr-xr-x 22 root root    4096 2007-08-29 20:17 ..
lrwxrwxrwx  1 root root      41 2007-08-29 13:19 2.6.22-sabayon -> /boot/kernel-genkernel-x86-2.6.22-sabayon
lrwxrwxrwx  1 root root       1 2007-08-29 12:46 boot -> .
drwxr-xr-x  2 root root    4096 2008-05-16 20:55 grub
-rw-r--r--  1 root root 3982427 2007-08-01 17:35 initramfs-genkernel-x86-2.6.22-sabayon
-rw-r--r--  1 root root 4349168 2007-08-01 17:18 kernel-genkernel-x86-2.6.22-sabayon
-rw-r--r--  1 root root 1633142 2007-08-01 17:18 System.map-genkernel-x86-2.6.22-sabayon
lrwxrwxrwx  1 root root      20 2007-08-29 13:19 vmlinuz -> /boot/2.6.22-sabayon

=============================== sdc8/boot/grub: ===============================

total 2088
drwxr-xr-x 2 root root   4096 2008-05-16 20:55 .
drwxr-xr-x 3 root root   4096 2007-08-29 13:19 ..
-rw-r--r-- 1 root root     30 2007-08-29 13:16 device.map
-rw-r--r-- 1 root root   7904 2006-08-20 10:31 e2fs_stage1_5
-rw-r--r-- 1 root root   7744 2006-08-20 10:31 fat_stage1_5
-rw-r--r-- 1 root root   7040 2006-08-20 10:31 ffs_stage1_5
-rw------- 1 root root   1267 2008-06-21 09:35 grub.conf
-rw-r--r-- 1 root root   1624 2006-08-20 10:31 grub.conf.sample
-rw-r--r-- 1 root root   7040 2006-08-20 10:31 iso9660_stage1_5
-rw-r--r-- 1 root root   8480 2006-08-20 10:31 jfs_stage1_5
lrwxrwxrwx 1 root root     11 2007-08-29 13:19 menu.lst -> ./grub.conf
lrwxrwxrwx 1 root root      9 2007-08-29 12:46 menu.lst.rpmsave -> grub.conf
-rw-r--r-- 1 root root   7200 2006-08-20 10:31 minix_stage1_5
-rw-r--r-- 1 root root   9504 2006-08-20 10:31 reiserfs_stage1_5
-rw-r--r-- 1 root root 142763 2007-09-13 13:41 splash-2.xcf
-rw-r--r-- 1 root root 309402 2007-09-13 13:40 splash-2.xpm
-rw-r--r-- 1 root root  26262 2007-09-09 19:17 splash.bak.xpm.gz
-rw-r--r-- 1 root root 371294 2007-09-13 13:12 splash.xcf
-rw-r--r-- 1 root root 624216 2007-09-13 13:11 splash.xpm
-rw-r--r-- 1 root root  28079 2007-09-13 13:41 splash.xpm.gz
-rw-r--r-- 1 root root  26262 2006-08-20 15:22 splash.xpm.gz.bak
-rw-r--r-- 1 root root    512 2006-08-20 10:31 stage1
-rw-r--r-- 1 root root 102748 2007-09-13 13:50 stage2
-rw-r--r-- 1 root root 102748 2007-09-13 12:05 stage2.bak
-rw-r--r-- 1 root root 102748 2006-08-20 10:31 stage2_eltorito
-rw-r--r-- 1 root root 102236 2006-07-25 06:18 stage2.old
-rw-r--r-- 1 root root   7392 2006-08-20 10:31 ufs2_stage1_5
-rw-r--r-- 1 root root   6592 2006-08-20 10:31 vstafs_stage1_5
-rw-r--r-- 1 root root   9224 2006-08-20 10:31 xfs_stage1_5

=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

I forgot to unplug my external hard drive first - oh well, there's some extra info there.

---

### Post by FIONEX on 2009-01-16
try using this first:
chainloader --force +1

The most likely problem is that your windows MBR is corrupt...So when you set chainloader +1, it goes to the windows MBR and stalls.  The funny part is that you'll probably need a 
startup disk and then run "fdisk /mbr", which will get your windows MBR back, but wipe out grub's boot record. After that, you can reinstall grub easily using a live cd.

---

### Post by slade on 2009-01-17
tried that.  twice.  no such luck.  after i ran the fixmbr command it said it worked, but when I rebooted it wouldn't boot into windows.  I reinstalled grub (and had a lot of trouble doing that - for some reason it wouldn't recognize stage1 and stage2 on my ubuntu partition, so i had to restore to the fedora partition first, then to ubuntu) and it still won't boot windows, so i'm back to stage 1.  any ideas?

(fdisk /mbr returned an error, so i ran the fixmbr command)

---

### Post by slade on 2009-01-17
okay, I tried "fixboot C:" and that didn't work either.  It did recognize the drive and looked like it worked, but no luck.

---

### Post by caljohnsmith on 2009-01-17
It looks like you need to fix the sda1 Windows boot sector, because currently the file system parameters in the boot sector are incorrect. Unfortunately "fixboot" will not fix those types of problems, but the good news is that "testdisk" can. To use testdisk, how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the sda1 Windows partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Also, please use the following entry to boot Windows in your Grub menu:
```
title Windows XP
rootnoverify (hd0,0)
ainloader +1
```
Let me know how that goes.

---

### Post by slade on 2009-01-17
I now get:

```
Starting up...

A disk read error occurred
Press Ctrl+Alt+Del to restart
```

---

### Post by caljohnsmith on 2009-01-17
Did you run the testdisk "Rebuild BS" procedure on the sda1 partition? Did it allow you to do the "Rebuild BS"? How about posting the results of the Boot Info Script again so I can get a better idea if testdisk worked or not.

---

### Post by slade on 2009-01-17
yes, I did all of that and it completed successfully.  It looks like it worked, but it still won't boot.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 10 (Cambridge) Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab 
                       /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 8 (Werewolf) Kernel on an
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab 
                       /boot /boot/grub

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda8 
                       and looks at sector 545065056 of the same hard drive 
                       for the stage2 file and on partition #8 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007f0ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62508914    31254426    7  HPFS/NTFS
/dev/sda2        62508915    87265079    12378082+  83  Linux
/dev/sda3        87265080   556845029   234789975    5  Extended
/dev/sda5        87265143    91458044     2096451   82  Linux swap / Solaris
/dev/sda6        91458108   113868719    11205306   83  Linux
/dev/sda7       113868783   532088864   209110041   83  Linux
/dev/sda8       532088928   556845029    12378051   83  Linux

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F6149ECE149E90EB" TYPE="ntfs" 
/dev/sda2: LABEL="F10" UUID="c460b2f0-736e-4054-a6d5-4460023a34aa" TYPE="ext3" 
/dev/sda5: UUID="42dd3d1d-6f42-04a3-aea9-956e638b3ccb" TYPE="swap" 
/dev/sda6: LABEL="/1" UUID="b822888a-bb1c-42cb-ab9d-cca3f01a4f55" TYPE="ext3" 
/dev/sda7: LABEL="SHARE" UUID="84ef4e00-0d43-42fb-b123-9b1f97019df1" TYPE="ext3" 
/dev/sda8: UUID="f21c98d3-2d4f-4513-9c7f-77c951a745dc" TYPE="ext3" 
/dev/mmcblk0p1: UUID="FC30-3DA9" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda2 on /mnt/F10 type ext3 (rw,relatime)
/dev/sda6 on /mnt/F8 type ext3 (rw,relatime)
/dev/sda1 on /mnt/XP type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7 on /share type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/colin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=colin)
/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================


========================== sda2/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,1)
#          kernel /boot/vmlinuz-version ro root=/dev/sda2
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.9-159.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.9-159.fc10.i686 ro root=UUID=c460b2f0-736e-4054-a6d5-4460023a34aa rhgb quiet
	initrd /boot/initrd-2.6.27.9-159.fc10.i686.img
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=c460b2f0-736e-4054-a6d5-4460023a34aa rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.i686.img
title Other
	rootnoverify (hd0,0)
	chainloader +1

=============================== sda2/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Fri Jan  2 00:44:29 2009
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or vol_id(8) for more info
#
UUID=c460b2f0-736e-4054-a6d5-4460023a34aa /                       ext3    defaults        1 1
UUID=84ef4e00-0d43-42fb-b123-9b1f97019df1 /share                  ext3    defaults        1 2
UUID=b822888a-bb1c-42cb-ab9d-cca3f01a4f55 /mnt/F8                 ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
LABEL=SWAP-sda5         swap                    swap    defaults        0 0

================================== sda2/boot: ==================================

total 13600
drwxr-xr-x  4 root root    4096 2009-01-01 14:27 .
drwxr-xr-x 23 root root    4096 2009-01-12 23:14 ..
-rw-r--r--  1 root root   90889 2008-11-18 09:30 config-2.6.27.5-117.fc10.i686
-rw-r--r--  1 root root   91102 2008-12-16 12:21 config-2.6.27.9-159.fc10.i686
drwxr-xr-x  3 root root    4096 2009-01-01 16:50 efi
drwxr-xr-x  2 root root    4096 2009-01-01 14:27 grub
-rw-------  1 root root 3161183 2009-01-01 16:52 initrd-2.6.27.5-117.fc10.i686.img
-rw-------  1 root root 3182706 2009-01-01 14:27 initrd-2.6.27.9-159.fc10.i686.img
-rw-r--r--  1 root root 1089949 2008-11-18 09:30 System.map-2.6.27.5-117.fc10.i686
-rw-r--r--  1 root root 1090858 2008-12-16 12:21 System.map-2.6.27.9-159.fc10.i686
-rwxr-xr-x  1 root root 2570960 2008-11-18 09:30 vmlinuz-2.6.27.5-117.fc10.i686
-rwxr-xr-x  1 root root 2575088 2008-12-16 12:21 vmlinuz-2.6.27.9-159.fc10.i686

=============================== sda2/boot/grub: ===============================

total 308
drwxr-xr-x 2 root root   4096 2009-01-01 14:27 .
drwxr-xr-x 4 root root   4096 2009-01-01 14:27 ..
-rw-r--r-- 1 root root     63 2009-01-01 17:00 device.map
-rw-r--r-- 1 root root  11736 2009-01-01 17:00 e2fs_stage1_5
-rw-r--r-- 1 root root  11512 2009-01-01 17:00 fat_stage1_5
-rw-r--r-- 1 root root  10744 2009-01-01 17:00 ffs_stage1_5
-rw------- 1 root root    914 2009-01-01 14:27 grub.conf
-rw-r--r-- 1 root root  10736 2009-01-01 17:00 iso9660_stage1_5
-rw-r--r-- 1 root root  12328 2009-01-01 17:00 jfs_stage1_5
lrwxrwxrwx 1 root root     11 2009-01-01 17:00 menu.lst -> ./grub.conf
-rw-r--r-- 1 root root  10968 2009-01-01 17:00 minix_stage1_5
-rw-r--r-- 1 root root  13360 2009-01-01 17:00 reiserfs_stage1_5
-rw-r--r-- 1 root root  40685 2008-10-24 07:40 splash.xpm.gz
-rw-r--r-- 1 root root    512 2009-01-01 17:00 stage1
-rw-r--r-- 1 root root 111004 2009-01-01 17:00 stage2
-rw-r--r-- 1 root root  11008 2009-01-01 17:00 ufs2_stage1_5
-rw-r--r-- 1 root root  10344 2009-01-01 17:00 vstafs_stage1_5
-rw-r--r-- 1 root root  12984 2009-01-01 17:00 xfs_stage1_5

=========================== sda6/boot/grub/menu.lst: ===========================


========================== sda6/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,1)
#          kernel /boot/vmlinuz-version ro root=/dev/sda8
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,5)/boot/grub/splash.xpm.gz
hiddenmenu

title Fedora (2.6.26.8-57.fc8)
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.26.8-57.fc8 ro root=/dev/sda6 rhgb quiet
	initrd /boot/initrd-2.6.26.8-57.fc8.img
title Ubuntu 8.10 (2.6.27-9-generic)
	root (hd0,7)
	kernel /boot/vmlinuz-2.6.27-9-generic root=/dev/sda8 ro quiet splash
	initrd /boot/initrd.img-2.6.27-9-generic

title Fedora (2.6.27.7-134.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.7-134.fc10.i686 ro root=/dev/sda2 rhgb quiet
	initrd /boot/initrd-2.6.27.7-134.fc10.i686.img


title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.i686 ro root=/dev/sda2 rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.i686.img


title Fedora (2.6.26.6-49.fc8)
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.26.6-49.fc8 ro root=LABEL=/1 rhgb quiet
	initrd /boot/initrd-2.6.26.6-49.fc8.img
title XP
	rootnoverify (hd0,0)
	chainloader +1

=============================== sda6/etc/fstab: ===============================

/dev/sda6               /                       ext3    defaults        1 1
/dev/sda2               /mnt/F10                ext3    defaults        1 2
/dev/sda7               /share                  ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sda5               swap                    swap    defaults        0 0

================================== sda6/boot: ==================================

total 12244
drwxr-xr-x  3 root root    4096 2009-01-16 14:07 .
drwxr-xr-x 24 root root    4096 2009-01-16 14:33 ..
-rw-r--r--  1 root root   88385 2008-10-17 13:10 config-2.6.26.6-49.fc8
-rw-r--r--  1 root root   88396 2008-12-18 16:27 config-2.6.26.8-57.fc8
drwxr-xr-x  2 root root    4096 2009-01-16 14:07 grub
-rw-------  1 root root 3059984 2008-10-24 02:51 initrd-2.6.26.6-49.fc8.img
-rw-------  1 root root 3058976 2009-01-16 14:06 initrd-2.6.26.8-57.fc8.img
-rw-r--r--  1 root root  934839 2008-10-17 13:10 System.map-2.6.26.6-49.fc8
-rw-r--r--  1 root root  934955 2008-12-18 16:27 System.map-2.6.26.8-57.fc8
-rw-r--r--  1 root root 2133568 2008-10-17 13:10 vmlinuz-2.6.26.6-49.fc8
-rw-r--r--  1 root root 2133920 2008-12-18 16:27 vmlinuz-2.6.26.8-57.fc8

=============================== sda6/boot/grub: ===============================

total 312
drwxr-xr-x 2 root root   4096 2009-01-16 14:07 .
drwxr-xr-x 3 root root   4096 2009-01-16 14:07 ..
-rw-r--r-- 1 root root     63 2008-06-21 14:33 device.map
-rw-r--r-- 1 root root   8096 2008-06-21 14:33 e2fs_stage1_5
-rw-r--r-- 1 root root   7936 2008-06-21 14:33 fat_stage1_5
-rw-r--r-- 1 root root   7200 2008-06-21 14:33 ffs_stage1_5
-rw------- 1 root root   1333 2009-01-16 14:07 grub.conf
-rw------- 1 root root   1237 2008-12-25 21:06 grub.conf~
-rw------- 1 root root   1572 2008-11-05 15:28 grub.conf.bak
-rw-r--r-- 1 root root   7200 2008-06-21 14:33 iso9660_stage1_5
-rw-r--r-- 1 root root   8672 2008-06-21 14:33 jfs_stage1_5
lrwxrwxrwx 1 root root     11 2008-06-21 14:33 menu.lst -> ./grub.conf
-rw-r--r-- 1 root root   7328 2008-06-21 14:33 minix_stage1_5
-rw-r--r-- 1 root root   9696 2008-06-21 14:33 reiserfs_stage1_5
-rw-r--r-- 1 root root   7459 2007-11-14 07:00 splash.xpm.gz
-rw-r--r-- 1 root root    512 2008-06-21 14:33 stage1
-rw-r--r-- 1 root root 105468 2008-06-21 14:33 stage2
-rw-r--r-- 1 root root   7520 2008-06-21 14:33 ufs2_stage1_5
-rw-r--r-- 1 root root   6752 2008-06-21 14:33 vstafs_stage1_5
-rw-r--r-- 1 root root   9344 2008-06-21 14:33 xfs_stage1_5

=========================== sda8/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f21c98d3-2d4f-4513-9c7f-77c951a745dc

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
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Fedora (2.6.26.6-49.fc8) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26.6-49.fc8 ro root=LABEL=/1 rhgb quiet 
initrd		/boot/initrd-2.6.26.6-49.fc8.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Fedora (2.6.25.14-69.fc8) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.25.14-69.fc8 ro root=LABEL=/1 rhgb quiet 
initrd		/boot/initrd-2.6.25.14-69.fc8.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Fedora (2.6.27.9-159.fc10.i686) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27.9-159.fc10.i686 ro root=UUID=c460b2f0-736e-4054-a6d5-4460023a34aa rhgb quiet 
initrd		/boot/initrd-2.6.27.9-159.fc10.i686.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Fedora (2.6.26.6-49.fc8) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.26.6-49.fc8 ro root=LABEL=/1 rhgb quiet 
initrd		/boot/initrd-2.6.26.6-49.fc8.img
savedefault
boot


title		XP
rootnoverify (hd0,0)
chainloader +1

title		XP
root		(hd0,0)
makeactive
chainloader	+1

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>      <options>                  <dump>  <pass>
proc            /proc           proc        defaults                   0       0
/dev/sda8       /               ext3        relatime,errors=remount-ro 0       1
/dev/sda2       /mnt/F10        ext3        relatime                   0       2
/dev/sda6       /mnt/F8         ext3        relatime                   0       2
/dev/sda1       /mnt/XP         ntfs        defaults,umask=007,gid=46  0       1
/dev/sda7       /share          ext3        relatime                   0       2
/dev/sda5       none            swap        sw                         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8      0       0

================================== sda8/boot: ==================================

total 23804
drwxr-xr-x  3 root root    4096 2009-01-13 03:13 .
drwxr-xr-x 21 root root    4096 2009-01-13 03:13 ..
-rw-r--r--  1 root root  507665 2008-11-04 13:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 15:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 13:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 15:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-13 03:13 grub
-rw-r--r--  1 root root 8203368 2009-01-13 03:12 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8202544 2009-01-13 03:13 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 13:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 13:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 15:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 13:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 15:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 13:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 15:46 vmlinuz-2.6.27-9-generic

=============================== sda8/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-13 03:13 .
drwxr-xr-x 3 root root   4096 2009-01-13 03:13 ..
-rw-r--r-- 1 root root    197 2009-01-13 02:46 default
-rw-r--r-- 1 root root     15 2009-01-13 02:46 device.map
-rw-r--r-- 1 root root   8108 2009-01-13 02:46 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-13 02:46 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-13 02:46 installed-version
-rw-r--r-- 1 root root   8712 2009-01-13 02:46 jfs_stage1_5
-rw-r--r-- 1 root root   6280 2009-01-17 13:34 menu.lst
-rw-r--r-- 1 root root   6723 2009-01-13 03:13 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-13 02:46 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-13 02:46 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-13 02:46 stage1
-rw-r--r-- 1 root root 121460 2009-01-13 02:46 stage2
-rw-r--r-- 1 root root   9556 2009-01-13 02:46 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by maybeway36 on 2009-01-17
Can you boot Windows from Fedora's GRUB? To get to it try from the GRUB command line:
```
configfile (hd0,1)/boot/grub/mneu.lst
```
To restore boot records and MBRs, the ms-sys package (attached) might help you. I built it myself from the source at [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/).

---

### Post by caljohnsmith on 2009-01-17
How about booting your Windows XP Install CD, go to the "recovery console" and do:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Then try booting XP again, and let me know exactly what happens.

---

### Post by slade on 2009-01-17
I tried booting from both fedora installs and got the same error every time.

```
chkdsk /r
```

found and fixed errors.  I ran it again, and it didn't find any errors the second time around.  however, I get the same error when I try booting.

what arguments would I need with the ms-sys package?  the documentation doesn't say anything about an NTFS file system.  I used:

```
fixboot C:
```
which theoretically should do the same thing, so I'm not sure if it would help.

I have a backup of the windows partition on an external HDD from a while ago, so I'd lose some things but I may try restoring that partition.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 10 (Cambridge) Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab 
                       /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 8 (Werewolf) Kernel on an
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab 
                       /boot /boot/grub

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda8 
                       and looks at sector 545065056 of the same hard drive 
                       for the stage2 file and on partition #8 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007f0ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62508914    31254426    7  HPFS/NTFS
/dev/sda2        62508915    87265079    12378082+  83  Linux
/dev/sda3        87265080   556845029   234789975    5  Extended
/dev/sda5        87265143    91458044     2096451   82  Linux swap / Solaris
/dev/sda6        91458108   113868719    11205306   83  Linux
/dev/sda7       113868783   532088864   209110041   83  Linux
/dev/sda8       532088928   556845029    12378051   83  Linux

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F6149ECE149E90EB" TYPE="ntfs" 
/dev/sda2: LABEL="F10" UUID="c460b2f0-736e-4054-a6d5-4460023a34aa" TYPE="ext3" 
/dev/sda5: UUID="42dd3d1d-6f42-04a3-aea9-956e638b3ccb" TYPE="swap" 
/dev/sda6: LABEL="/1" UUID="b822888a-bb1c-42cb-ab9d-cca3f01a4f55" TYPE="ext3" 
/dev/sda7: LABEL="SHARE" UUID="84ef4e00-0d43-42fb-b123-9b1f97019df1" TYPE="ext3" 
/dev/sda8: UUID="f21c98d3-2d4f-4513-9c7f-77c951a745dc" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda2 on /mnt/F10 type ext3 (rw,relatime)
/dev/sda6 on /mnt/F8 type ext3 (rw,relatime)
/dev/sda1 on /mnt/XP type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7 on /share type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/colin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=colin)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================


========================== sda2/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,1)
#          kernel /boot/vmlinuz-version ro root=/dev/sda2
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.9-159.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.9-159.fc10.i686 ro root=UUID=c460b2f0-736e-4054-a6d5-4460023a34aa rhgb quiet
	initrd /boot/initrd-2.6.27.9-159.fc10.i686.img
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=c460b2f0-736e-4054-a6d5-4460023a34aa rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.i686.img
title Other
	rootnoverify (hd0,0)
	chainloader +1

=============================== sda2/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Fri Jan  2 00:44:29 2009
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or vol_id(8) for more info
#
UUID=c460b2f0-736e-4054-a6d5-4460023a34aa /                       ext3    defaults        1 1
UUID=84ef4e00-0d43-42fb-b123-9b1f97019df1 /share                  ext3    defaults        1 2
UUID=b822888a-bb1c-42cb-ab9d-cca3f01a4f55 /mnt/F8                 ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
LABEL=SWAP-sda5         swap                    swap    defaults        0 0

================================== sda2/boot: ==================================

total 13600
drwxr-xr-x  4 root root    4096 2009-01-01 14:27 .
drwxr-xr-x 23 root root    4096 2009-01-12 23:14 ..
-rw-r--r--  1 root root   90889 2008-11-18 09:30 config-2.6.27.5-117.fc10.i686
-rw-r--r--  1 root root   91102 2008-12-16 12:21 config-2.6.27.9-159.fc10.i686
drwxr-xr-x  3 root root    4096 2009-01-01 16:50 efi
drwxr-xr-x  2 root root    4096 2009-01-01 14:27 grub
-rw-------  1 root root 3161183 2009-01-01 16:52 initrd-2.6.27.5-117.fc10.i686.img
-rw-------  1 root root 3182706 2009-01-01 14:27 initrd-2.6.27.9-159.fc10.i686.img
-rw-r--r--  1 root root 1089949 2008-11-18 09:30 System.map-2.6.27.5-117.fc10.i686
-rw-r--r--  1 root root 1090858 2008-12-16 12:21 System.map-2.6.27.9-159.fc10.i686
-rwxr-xr-x  1 root root 2570960 2008-11-18 09:30 vmlinuz-2.6.27.5-117.fc10.i686
-rwxr-xr-x  1 root root 2575088 2008-12-16 12:21 vmlinuz-2.6.27.9-159.fc10.i686

=============================== sda2/boot/grub: ===============================

total 308
drwxr-xr-x 2 root root   4096 2009-01-01 14:27 .
drwxr-xr-x 4 root root   4096 2009-01-01 14:27 ..
-rw-r--r-- 1 root root     63 2009-01-01 17:00 device.map
-rw-r--r-- 1 root root  11736 2009-01-01 17:00 e2fs_stage1_5
-rw-r--r-- 1 root root  11512 2009-01-01 17:00 fat_stage1_5
-rw-r--r-- 1 root root  10744 2009-01-01 17:00 ffs_stage1_5
-rw------- 1 root root    914 2009-01-01 14:27 grub.conf
-rw-r--r-- 1 root root  10736 2009-01-01 17:00 iso9660_stage1_5
-rw-r--r-- 1 root root  12328 2009-01-01 17:00 jfs_stage1_5
lrwxrwxrwx 1 root root     11 2009-01-01 17:00 menu.lst -> ./grub.conf
-rw-r--r-- 1 root root  10968 2009-01-01 17:00 minix_stage1_5
-rw-r--r-- 1 root root  13360 2009-01-01 17:00 reiserfs_stage1_5
-rw-r--r-- 1 root root  40685 2008-10-24 07:40 splash.xpm.gz
-rw-r--r-- 1 root root    512 2009-01-01 17:00 stage1
-rw-r--r-- 1 root root 111004 2009-01-01 17:00 stage2
-rw-r--r-- 1 root root  11008 2009-01-01 17:00 ufs2_stage1_5
-rw-r--r-- 1 root root  10344 2009-01-01 17:00 vstafs_stage1_5
-rw-r--r-- 1 root root  12984 2009-01-01 17:00 xfs_stage1_5

=========================== sda6/boot/grub/menu.lst: ===========================


========================== sda6/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,1)
#          kernel /boot/vmlinuz-version ro root=/dev/sda8
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,5)/boot/grub/splash.xpm.gz
hiddenmenu

title Fedora (2.6.26.8-57.fc8)
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.26.8-57.fc8 ro root=/dev/sda6 rhgb quiet
	initrd /boot/initrd-2.6.26.8-57.fc8.img
title Ubuntu 8.10 (2.6.27-9-generic)
	root (hd0,7)
	kernel /boot/vmlinuz-2.6.27-9-generic root=/dev/sda8 ro quiet splash
	initrd /boot/initrd.img-2.6.27-9-generic

title Fedora (2.6.27.7-134.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.7-134.fc10.i686 ro root=/dev/sda2 rhgb quiet
	initrd /boot/initrd-2.6.27.7-134.fc10.i686.img


title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.i686 ro root=/dev/sda2 rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.i686.img


title Fedora (2.6.26.6-49.fc8)
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.26.6-49.fc8 ro root=LABEL=/1 rhgb quiet
	initrd /boot/initrd-2.6.26.6-49.fc8.img
title XP
	rootnoverify (hd0,0)
	chainloader +1

=============================== sda6/etc/fstab: ===============================

/dev/sda6               /                       ext3    defaults        1 1
/dev/sda2               /mnt/F10                ext3    defaults        1 2
/dev/sda7               /share                  ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sda5               swap                    swap    defaults        0 0

================================== sda6/boot: ==================================

total 12244
drwxr-xr-x  3 root root    4096 2009-01-16 14:07 .
drwxr-xr-x 24 root root    4096 2009-01-16 14:33 ..
-rw-r--r--  1 root root   88385 2008-10-17 13:10 config-2.6.26.6-49.fc8
-rw-r--r--  1 root root   88396 2008-12-18 16:27 config-2.6.26.8-57.fc8
drwxr-xr-x  2 root root    4096 2009-01-16 14:07 grub
-rw-------  1 root root 3059984 2008-10-24 02:51 initrd-2.6.26.6-49.fc8.img
-rw-------  1 root root 3058976 2009-01-16 14:06 initrd-2.6.26.8-57.fc8.img
-rw-r--r--  1 root root  934839 2008-10-17 13:10 System.map-2.6.26.6-49.fc8
-rw-r--r--  1 root root  934955 2008-12-18 16:27 System.map-2.6.26.8-57.fc8
-rw-r--r--  1 root root 2133568 2008-10-17 13:10 vmlinuz-2.6.26.6-49.fc8
-rw-r--r--  1 root root 2133920 2008-12-18 16:27 vmlinuz-2.6.26.8-57.fc8

=============================== sda6/boot/grub: ===============================

total 312
drwxr-xr-x 2 root root   4096 2009-01-16 14:07 .
drwxr-xr-x 3 root root   4096 2009-01-16 14:07 ..
-rw-r--r-- 1 root root     63 2008-06-21 14:33 device.map
-rw-r--r-- 1 root root   8096 2008-06-21 14:33 e2fs_stage1_5
-rw-r--r-- 1 root root   7936 2008-06-21 14:33 fat_stage1_5
-rw-r--r-- 1 root root   7200 2008-06-21 14:33 ffs_stage1_5
-rw------- 1 root root   1333 2009-01-16 14:07 grub.conf
-rw------- 1 root root   1237 2008-12-25 21:06 grub.conf~
-rw------- 1 root root   1572 2008-11-05 15:28 grub.conf.bak
-rw-r--r-- 1 root root   7200 2008-06-21 14:33 iso9660_stage1_5
-rw-r--r-- 1 root root   8672 2008-06-21 14:33 jfs_stage1_5
lrwxrwxrwx 1 root root     11 2008-06-21 14:33 menu.lst -> ./grub.conf
-rw-r--r-- 1 root root   7328 2008-06-21 14:33 minix_stage1_5
-rw-r--r-- 1 root root   9696 2008-06-21 14:33 reiserfs_stage1_5
-rw-r--r-- 1 root root   7459 2007-11-14 07:00 splash.xpm.gz
-rw-r--r-- 1 root root    512 2008-06-21 14:33 stage1
-rw-r--r-- 1 root root 105468 2008-06-21 14:33 stage2
-rw-r--r-- 1 root root   7520 2008-06-21 14:33 ufs2_stage1_5
-rw-r--r-- 1 root root   6752 2008-06-21 14:33 vstafs_stage1_5
-rw-r--r-- 1 root root   9344 2008-06-21 14:33 xfs_stage1_5

=========================== sda8/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f21c98d3-2d4f-4513-9c7f-77c951a745dc

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
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f21c98d3-2d4f-4513-9c7f-77c951a745dc ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f21c98d3-2d4f-4513-9c7f-77c951a745dc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Fedora (2.6.26.6-49.fc8) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26.6-49.fc8 ro root=LABEL=/1 rhgb quiet 
initrd		/boot/initrd-2.6.26.6-49.fc8.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Fedora (2.6.25.14-69.fc8) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.25.14-69.fc8 ro root=LABEL=/1 rhgb quiet 
initrd		/boot/initrd-2.6.25.14-69.fc8.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Fedora (2.6.27.9-159.fc10.i686) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27.9-159.fc10.i686 ro root=UUID=c460b2f0-736e-4054-a6d5-4460023a34aa rhgb quiet 
initrd		/boot/initrd-2.6.27.9-159.fc10.i686.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Fedora (2.6.26.6-49.fc8) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.26.6-49.fc8 ro root=LABEL=/1 rhgb quiet 
initrd		/boot/initrd-2.6.26.6-49.fc8.img
savedefault
boot


title		XP
rootnoverify (hd0,0)
chainloader +1

title		XP
root		(hd0,0)
makeactive
chainloader	+1

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>      <options>                  <dump>  <pass>
proc            /proc           proc        defaults                   0       0
/dev/sda8       /               ext3        relatime,errors=remount-ro 0       1
/dev/sda2       /mnt/F10        ext3        relatime                   0       2
/dev/sda6       /mnt/F8         ext3        relatime                   0       2
/dev/sda1       /mnt/XP         ntfs        defaults,umask=007,gid=46  0       1
/dev/sda7       /share          ext3        relatime                   0       2
/dev/sda5       none            swap        sw                         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8      0       0

================================== sda8/boot: ==================================

total 23804
drwxr-xr-x  3 root root    4096 2009-01-13 03:13 .
drwxr-xr-x 21 root root    4096 2009-01-13 03:13 ..
-rw-r--r--  1 root root  507665 2008-11-04 13:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 15:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 13:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 15:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-13 03:13 grub
-rw-r--r--  1 root root 8203368 2009-01-13 03:12 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8202544 2009-01-13 03:13 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 13:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 13:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 15:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 13:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 15:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 13:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 15:46 vmlinuz-2.6.27-9-generic

=============================== sda8/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-13 03:13 .
drwxr-xr-x 3 root root   4096 2009-01-13 03:13 ..
-rw-r--r-- 1 root root    197 2009-01-13 02:46 default
-rw-r--r-- 1 root root     15 2009-01-13 02:46 device.map
-rw-r--r-- 1 root root   8108 2009-01-13 02:46 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-13 02:46 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-13 02:46 installed-version
-rw-r--r-- 1 root root   8712 2009-01-13 02:46 jfs_stage1_5
-rw-r--r-- 1 root root   6280 2009-01-17 13:34 menu.lst
-rw-r--r-- 1 root root   6723 2009-01-13 03:13 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-13 02:46 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-13 02:46 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-13 02:46 stage1
-rw-r--r-- 1 root root 121460 2009-01-13 02:46 stage2
-rw-r--r-- 1 root root   9556 2009-01-13 02:46 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by slade on 2009-01-18
no luck with that drive either.  I tried googling this error and found only a few results, without any solution.  It looks like I may just have to reinstall.

---

### Post by caljohnsmith on 2009-01-18
Since it looks like a reinstall may be the only solution, before you do that how about booting your Windows CD and doing:
```
fixmbr
```
That will replace Grub with a Windows MBR; I have seen a few rare cases in the forums where Grub could not boot Windows, but booting Windows with a Windows MBR worked. If it does work, you could add Grub to your Windows boot loader in order to keep the Windows MBR. If it doesn't work, you can reinstall Grub with:
```
sudo grub
grub> root (hd0,7)
grub> setup (hd0)
grub> quit
```
So if you're up for it, how about giving the "fixmbr" a shot and let me know how it goes.

---

### Post by Dieseler on 2009-01-18
I couldn't help but notice that you have XP listed twice in menu.lst.

> title		XP
rootnoverify (hd0,0)
chainloader +1

title		XP
root		(hd0,0)
makeactive
chainloader	+1

I'm not sure that it matters but it can't help matters I would think.

---

### Post by slade on 2009-01-18
well, it can't hurt.  I had it listed twice because one way was the method I learned a long while ago and the other way was the format listed in the ubuntu menu.lst comments.  I got the same error before and after I added the second entry.

I already tried fixmbr and it didn't work.  I'm backing up all my data now, but before I reinstall I'll give fixboot and fixmbr another shot.  I really don't want to have to reinstall, because it's about a 5 hour process for XP instead of a 1 hour process for linux, but it doesn't look like I have much of an option...

---

### Post by caljohnsmith on 2009-01-18
Have you tried the "Repair MFT" option for the Windows partition in testdisk? It would only take a minute to see if testdisk can find anything wrong with Windows MFT (Master File Table), and if it does, it might be able to fix it. To try it:
```
sudo testdisk

```
Choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the sda1 Windows partition, choose "Boot", then choose "Repair MFT"; let me know what testdisk reports when you try that option, and if testdisk gives you the option to fix the MFT, how about trying it. Let me know how that goes.

---

### Post by slade on 2009-01-18
repair MFT fixed an error, and I ran it again with no errors, but I get the same error when trying to boot.

---

### Post by rMatey on 2009-01-18
Try using Super Grub Disk.

  I was having all kinds of problems, but got mine fixed.....  not really sure if I did switch the sata or not.
  read here:
[http://ubuntuforums.org/showthread.php?t=1040802](http://ubuntuforums.org/showthread.php?t=1040802)

  Super Grub makes it easy to do the repairs, or boot into an operating system even if the boot get squished.

---

### Post by slade on 2009-01-19
well, the reinstall worked.  when I ran the reinstall, the CD wouldn't even recognize the previous install as NTFS (although linux was able to salvage the data).  Let's just hope it doesn't happen again.

---

