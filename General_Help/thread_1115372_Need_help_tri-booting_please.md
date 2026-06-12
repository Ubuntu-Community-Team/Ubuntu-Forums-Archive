---
title: "Need help tri-booting please"
date: 2009-04-03
forum: General Help
---

### Post by Predtech on 2009-04-03
Hi guys. i currently run Ubuntu Intrepid 64bit and I have the installation on a SATA 160GB drive which is partitioned into 67GB for ubuntu, 80GB for Mac OS X Leopard and 2GB for SWAP.
My boot/grub/menu.lst file looks like this:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5

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
uuid		a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		a4f8022b-a0cd-4def-bd4c-21ec7c7c50f5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

# on /dev/sdd2
title           MacOSX Leopard
root            (hd0,1)
chainloader     --force +1


According to my fstab file and blkid and Gparted my installs are both on sdd.
When booting, if i choose Windows or Leopard i just get error 18 on Leopard and the  "starting" quote for windows just stays on screen and never changes.

Can someone please help me figure out what i am doing wrong so i can get everything booting correctly from Grub.

Thanks

---

### Post by Predtech on 2009-04-04
Bump!

---

### Post by uidb4056 on 2009-04-04
In windows you should try to replace hd2,0 by hd0,2 and for Mac hd0,1 by hd0,3

Otherwise post the output of 'sudo fdisk-l' from terminal

---

### Post by Predtech on 2009-04-04
> **uidb4056 said:**
> In windows you should try to replace hd2,0 by hd0,2 and for Mac hd0,1 by hd0,3

Otherwise post the output of 'sudo fdisk-l' from terminal

Before i go and change anything i made an output of fdisk -l

richi@richi-desktop:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3a2eb81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30514   245103673+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55d3cbf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003eabc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001   af  Unknown
/dev/sdc2           60802      121601   488376000    7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1a96

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        8753    70308441   83  Linux
/dev/sdd2   *        8754       19196    83883397+  af  Unknown
/dev/sdd3           19197       19457     2096482+  82  Linux swap / Solaris

should i make the changes you recommended now?

---

### Post by Predtech on 2009-04-04
So i changed the windwos part to say
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
chainloader +1

Now i can boot into windows no problem.
Now i can't understand why i can't boot into OS X. 
I know it's on the same drive as Ubuntu, and it's the second partition so that should make it (hd0,1) and i have it like that in menu.lst but i still can't get into it.

Any other ideas?

---

### Post by Predtech on 2009-04-04
Bump!

---

