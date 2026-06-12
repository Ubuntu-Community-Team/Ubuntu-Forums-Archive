---
title: "Boot problems after update"
date: 2009-02-16
forum: Desktop Environments
---

### Post by arigwapo on 2009-02-16
I'm running 8.10 off of an Atom-based server.  No other OS is installed.  I recently updated my install and it asked me to reboot.  After rebooting, this appears:

Boot from (hd0,0) ext3 d89366b9-dc3c-42b6-8ea2-abbaef538691
Error 24: Attempt to access block outside partition
Press any key to continue...

Next page shows:

Ubuntu 8.10, kernel 2.6.27-11-generic
Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest86+

The first two selections don't work (goes back to the Error 24 screen) but the third one works fine.  

I'm totally clueless with Ubuntu/Linux so I need step-by-step instructions.  I've tried the various recommendations using a Live CD but haven't gotten it to work.  Any ideas how to fix it??

---

### Post by arigwapo on 2009-02-16
Anyone??

---

### Post by arigwapo on 2009-02-16
Here are the results of Boot Info Script if any one cares to read them:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d2f31

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 2,924,279,819 2,924,279,757  83 Linux
/dev/sda2       2,924,279,820 2,930,272,064     5,992,245   5 Extended
/dev/sda5       2,924,279,883 2,930,272,064     5,992,182  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 1030 MB, 1030750208 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2013184 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00058282

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,013,164     2,013,102   b W95 FAT32

/dev/sdb1 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="d89366b9-dc3c-42b6-8ea2-abbaef538691" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="7c4668fb-4df1-4e09-8a0e-9dc2ffbd5ab1" TYPE="swap" 
/dev/sdb1: LABEL="UNTITLED" UUID="3154-1112" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="1a0e3095-ae05-4f60-aec4-294fd5d4a120" TYPE="ext3" 

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
/dev/sdb1 on /cdrom type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
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
# kopt=root=UUID=d89366b9-dc3c-42b6-8ea2-abbaef538691 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d89366b9-dc3c-42b6-8ea2-abbaef538691

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
uuid		d89366b9-dc3c-42b6-8ea2-abbaef538691
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d89366b9-dc3c-42b6-8ea2-abbaef538691 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		d89366b9-dc3c-42b6-8ea2-abbaef538691
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d89366b9-dc3c-42b6-8ea2-abbaef538691 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		d89366b9-dc3c-42b6-8ea2-abbaef538691
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d89366b9-dc3c-42b6-8ea2-abbaef538691 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		d89366b9-dc3c-42b6-8ea2-abbaef538691
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d89366b9-dc3c-42b6-8ea2-abbaef538691 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d89366b9-dc3c-42b6-8ea2-abbaef538691
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d89366b9-dc3c-42b6-8ea2-abbaef538691 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d89366b9-dc3c-42b6-8ea2-abbaef538691
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d89366b9-dc3c-42b6-8ea2-abbaef538691 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d89366b9-dc3c-42b6-8ea2-abbaef538691
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d89366b9-dc3c-42b6-8ea2-abbaef538691 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7c4668fb-4df1-4e09-8a0e-9dc2ffbd5ab1 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 964.8GB: boot/grub/menu.lst
 893.1GB: boot/grub/stage2
 964.9GB: boot/initrd.img-2.6.27-11-generic
 893.1GB: boot/initrd.img-2.6.27-7-generic
 893.1GB: boot/initrd.img-2.6.27-9-generic
1212.0GB: boot/vmlinuz-2.6.27-11-generic
 893.1GB: boot/vmlinuz-2.6.27-7-generic
 893.1GB: boot/vmlinuz-2.6.27-9-generic
 964.9GB: initrd.img
 893.1GB: initrd.img.old
1212.0GB: vmlinuz
 893.1GB: vmlinuz.old
```

---

### Post by arigwapo on 2009-02-17
Anyone?

---

### Post by arigwapo on 2009-02-17
Or should I just reformat??  Maybe move to XP?

---

