---
title: "Re-enable GRUB"
date: 2008-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by teeshep on 2008-04-23
Hi. I bought a Dell Inspiron 1520 a while back, with Vista preloaded on it.
A while later, I decided to try Ubuntu. I installed it, and everything worked fine - dual booting Vista and Gutsy, using GRUB bootloader.
So I decided to upgrade from Vista to XP. I formatted my Vista partition, and installed XP on it. Everything seems to work fine.
EXCEPT
The installation of XP disabled GRUB. Now I have no bootloader to choose Ubuntu with, so now my computer automatically boots into XP. 
I'm looking for a way to re-enable it, but so far, to no avail. I still have the 7.10 live cd, if there is any way to do it using that.
I want to be able to use my Linux again, but I do NOT want to have to format the Ubuntu partition! Please help!

---

### Post by petzworld999 on 2008-04-23
Try this.

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by aidave on 2008-04-24
Also a bootable CD called "SuperGRUB" has saved me many times, if the GRUB command line is too much for you.

---

### Post by drsaamah on 2008-04-24
OR, if you're not in a rush, I would format the hard drive, install whatever version of Windows and THEN install Ubuntu.  When windows is installed it likes to take over the boot sequence. If Ubuntu is installed after Windows however, GRUB will be the primary bootloader and WILL let you pick between Windows or Ubuntu when you boot up.

---

### Post by teeshep on 2008-05-22
```
grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2 /bo
ot/grub/menu.lst"... failed

Error 22: No such partition

grub> 
```

It didn't work, what should I do?

Also, the problem is not that my HD is not mounted... well, I guess that's obvious from the fact that it finds the (hd0,5)... but anyways... it appears on my desktop as well as in Places > Computer, and I can open it and browse files etc. HELP

---

### Post by meierfra. on 2008-05-22
post the output of

```
sudo fdisk -l
```

---

### Post by teeshep on 2008-05-22
```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12       14462   116077657+   7  HPFS/NTFS
/dev/sda3           14463       19458    40122978+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4           19131       19458     2620416   dd  Unknown
Partition 4 does not end on cylinder boundary.
/dev/sda5           14463       16893    19526976   83  Linux

```

---

### Post by meierfra. on 2008-05-22
Something is wrong with you partition table.  "find /boot/grub/stage1" returns (hd0,5). Now (hd0,5) corresponds to /dev/sda6. But according the "fdisk" /dev/sda6 does not exist. It might have to do with the "omitting empty partition 5". I suggest to use "testdisk" to fix your partition table. You can install "testdisk" via "sudo apt-get install testdisk". For information on testdisk see my signature.

Do you know anything about "/dev/sda4" ?

---

### Post by teeshep on 2008-05-22
wow okay i am relatively new at this whole thing - this is WAY over my head.
and i have no idea about /dev/sda4.

---

### Post by meierfra. on 2008-05-22
Do you have a MediaDirect button on your laptop? (that would explain /dev/sda4)?

---

### Post by teeshep on 2008-05-22
I do have a set of media direct buttons.

---

### Post by meierfra. on 2008-05-23
You might try reinstalling ubuntu as an easy fix, but I'm not sure whether that will solve your problem. I believe that the "empty partition (5)" is causing all your problems. And reinstalling might not get rid of the "empty partition".  

Could you run the partition editor:

```
gksudo gparted
```

and post a screen shot? Maybe that helps to figure out what is going on.

---

### Post by teeshep on 2008-07-27
Finally i have managed to find the time to re-attempt this.

I used supergrub, tried "fix linux boot" or whatever it is... didn't work.
but i CAN use it to boot into my linux partition.
So...
```
teeshep@GERTRUDE-UBUNTU:~$ gksudo gparted
/home/teeshep/.themes/Green Glass2/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/teeshep/.themes/Green Glass2/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/teeshep/.themes/Green Glass2/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
teeshep@GERTRUDE-UBUNTU:~$ 

```

any suggestions?

Oh. and i 'gksudo gedit /boot/grub/menu.lst' and it still says:

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
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

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
# kopt=root=UUID=52a9553d-e522-4d4e-9266-4e5843b332a5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=52a9553d-e522-4d4e-9266-4e5843b332a5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=52a9553d-e522-4d4e-9266-4e5843b332a5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
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
# on /dev/sda3
title		Windows Vista
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```

By the way... I have uninstalled Vista and installed XP
which is why this is so messed up in the first place.
Thanks!

---

