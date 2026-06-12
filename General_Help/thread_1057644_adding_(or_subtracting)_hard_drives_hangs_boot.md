---
title: "adding (or subtracting) hard drives hangs boot"
date: 2009-02-02
forum: General Help
---

### Post by zzelinski on 2009-02-02
Had a Hardy Heron install, /home on a separate hard drive, and a third drive for more storage. (All IDE)

Third drive failed. I could start with failed drive in, hit f4 to accept that it failed, and then load ubuntu anyway. If I removed the drive, however, ubuntu hangs on boot --> loading screen, then blank black screen. Nothing works, have to shut down and restart with bad drive connected.

So, I buy a new replacement drive (was gonna anyway). I try to put that one in place of the old dead one. Same boot hang problem. So, I disconnect all other drives, and reinstall ubuntu to the OS disk I had before (now all alone in the computer). Once that's done, I connect up the two working drives. Now it hangs again.

One more note -- if I select the recovery mode from GRUB in the beginning, it loads and gives me a screen where i can continue normal boot, fix broken packages, try to fix xserver, etc. I select continue normal boot, and it works fine!

Please help me -- give me some idea of what the deal is -- why does ubuntu freak out when I change drives? I've not had this happen before.

Thanks!

---

### Post by zzelinski on 2009-02-02
bump -- any ideas?

---

### Post by Yellow Pasque on 2009-02-02
Can you post some info? Run these commands:
```
sudo fdisk -l
cat /etc/fstab
cat /boot/grub/menu.lst
```

---

### Post by zzelinski on 2009-02-02
> **Temüjin said:**
> Can you post some info? Run these commands:
```
sudo fdisk -l
cat /etc/fstab
cat /boot/grub/menu.lst
```

Hey thanks for responding! Ok here's the output for those commands:

fdisk -l
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3cd6afd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30217   242718021   83  Linux
/dev/sda2           30218       30401     1477980    5  Extended
/dev/sda5           30218       30401     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006047b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09ec0772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401   83  Linux

```


fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c6229288-eb5e-41b7-bd0d-126d17971bfe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2ad917c3-4394-4af2-b1cb-c82703971848 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#mounting separate /home directory from sdb1
/dev/sdb1    /home    ext3    nodev,nosuid    0    2
#mounting third drive as extra space for FTP
#/dev/sdc1    /home/fileserver/fileserver/FOLDERNAMEHERE    ext3    nodev,nosuid    0    2

```


menu.lst
```

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
#      password --md5 ****I TOOK THIS OUT, DON'T KNOW ENOUGH TO KNOW IF IT'S SAFE TO LEAVE IN****
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
# kopt=root=UUID=c6229288-eb5e-41b7-bd0d-126d17971bfe ro

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=c6229288-eb5e-41b7-bd0d-126d17971bfe ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=c6229288-eb5e-41b7-bd0d-126d17971bfe ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c6229288-eb5e-41b7-bd0d-126d17971bfe ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c6229288-eb5e-41b7-bd0d-126d17971bfe ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```


Thanks again, I hope this helps...I glanced over the output but don't know enough on my own to pinpoint issues.

---

