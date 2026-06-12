---
title: "Grub Error on 9.04"
date: 2009-04-28
forum: General Help
---

### Post by uchacker11 on 2009-04-28
I just installed Ubuntu 9.04 on my computer and cant get it to boot.  I initially installed it and got Grub error 17.  I downloaded the 64-bit version and am now getting Error 15 on the same computer.

I tried to follow this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351), but it still doesnt work.

I then tried to get LILO installed, but i cant figure that out either.  Please help.

---

### Post by codeseer on 2009-04-28
Post the results.txt from running this as sudo:

[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")

Edit:

Remember to put CODE tags around the results by selecting them and clicking the # button.

---

### Post by uchacker11 on 2009-04-28
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 7545202 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders, total 156312576 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     3,903,794     3,903,732  82 Linux swap / Solaris
/dev/sda2           3,903,795   156,312,449   152,408,655   5 Extended
/dev/sda5    *      3,903,858   156,312,449   152,408,592  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c879c87

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="fb9946cf-540a-4289-9d42-491f835eb5db" TYPE="swap" 
/dev/sda5: UUID="5d3a8bfb-a31e-469c-bca3-6d8c8c46cd46" TYPE="ext4" 
/dev/sdb1: UUID="32C0ACE4C0ACB011" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
# kopt=root=UUID=5d3a8bfb-a31e-469c-bca3-6d8c8c46cd46 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5d3a8bfb-a31e-469c-bca3-6d8c8c46cd46

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		5d3a8bfb-a31e-469c-bca3-6d8c8c46cd46
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5d3a8bfb-a31e-469c-bca3-6d8c8c46cd46 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		5d3a8bfb-a31e-469c-bca3-6d8c8c46cd46
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5d3a8bfb-a31e-469c-bca3-6d8c8c46cd46 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		5d3a8bfb-a31e-469c-bca3-6d8c8c46cd46
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=5d3a8bfb-a31e-469c-bca3-6d8c8c46cd46 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=fb9946cf-540a-4289-9d42-491f835eb5db none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   8.5GB: boot/grub/menu.lst
   3.8GB: boot/grub/stage2
   8.5GB: boot/initrd.img-2.6.28-11-generic
   3.9GB: boot/vmlinuz-2.6.28-11-generic
   8.5GB: initrd.img
   3.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by codeseer on 2009-04-28
What, exactly, is happening at this moment when you try to boot into Ubuntu?

---

### Post by uchacker11 on 2009-04-28
when I try and boot ubuntu everything posts and when grub is supposed to load i get the following error:

"GRUB Loading stage1.5.

GRUB loading, please wait...
Error 15
_"

and it will stay like that forever, i have tried reinstallation and 2 different medias.  All I can do is boot with a Live CD.

---

### Post by codeseer on 2009-04-28
Is the drive with Ubuntu on it or the drive with XP on it the one that has boot priority in the BIOS?

---

### Post by uchacker11 on 2009-04-28
the drive with Ubuntu on it

---

### Post by codeseer on 2009-04-28
What did it give you when you did:

```
find /boot/grub/stage1
```

---

### Post by uchacker11 on 2009-04-28
(hd0,4)

---

### Post by codeseer on 2009-04-28
So, you did:

```

> root (hd0,4)
> setup (hd0)
> quit

```

...and it didn't error?

Edit:

How did you end up getting the MBR of the second drive (XP) written with Grub?

---

### Post by uchacker11 on 2009-04-28
correct it said that the operation was successful but when I restart it doesnt boot

---

### Post by uchacker11 on 2009-04-28
XP isnt really installed, it is the remnants of an old install that is no longer used.  I just havent gotten the data I need off the drive in order to format it yet.

---

### Post by codeseer on 2009-04-28
Will it boot to recovery mode if you select that?

You might try more explicit declarations in the menu.lst file by changing this:

```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5d3a8bfb-a31e-469c-bca3-6d8c8c46cd46 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5d3a8bfb-a31e-469c-bca3-6d8c8c46cd46

```

...to this:

```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
**# kopt=root=/dev/sda5 ro**

## default grub root device
## e.g. groot=(hd0,0)
**# groot=(hd0,4)**

```

---

### Post by lindsay7 on 2009-04-28
Question for Codeseer.


You said to run this as sudo "/media/disk/boot_info_script032.sh"

Can you tell me how you do that? It does not work for me that way.

---

### Post by bumanie on 2009-04-28
As of [8.10]("http://users.bigpond.net.au/hermanzone/p15.htm"), the most common reason one gets a grub error 17 is due to a filesystem problem, rather than needing to reinstall grub. Try this code from a live cd. As far as I know the code works with ext4 as it did with ext2 and ext3> sudo e2fsck -C0 -p -f -v /dev/sdxx replacing the xx with your drive letter and number - in your case /dev/sda5.

---

### Post by uchacker11 on 2009-04-28
OK I got it to boot finally after removing the other HDD (the one with XP remnants).  Hopefully it will work after I get what I need and format it.

Thanks alot Codeseer for all your help.

---

### Post by codeseer on 2009-04-28
> **uchacker11 said:**
> OK I got it to boot finally after removing the other HDD (the one with XP remnants).  Hopefully it will work after I get what I need and format it.

Thanks alot Codeseer for all your help.

Great! I kept thinking it was pretty odd.

---

### Post by codeseer on 2009-04-28
> **lindsay7 said:**
> Question for Codeseer.


You said to run this as sudo "/media/disk/boot_info_script032.sh"

Can you tell me how you do that? It does not work for me that way.

You open a terminal and basically 'cd' to wherever you downloaded it and type this:

```
sudo ./boot*.sh
```

---

