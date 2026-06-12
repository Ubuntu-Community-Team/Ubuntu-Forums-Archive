---
title: "GRUB splashimage not displaying"
date: 2009-06-07
forum: General Help
---

### Post by solidsnake204 on 2009-06-07
I have created a splashimage which I want to use on my old PC which uses GRUB as it's bootloader.

I know there is nothing wrong with the image as I have applied it to GRUB inside a virtual machine, and it works flawlessly.

But on my old PC, it just doesn't show.

I have the image, breeze.xpm.gz, in the /boot/grub/ folder.
I have the /boot on a separate partition to Ubuntu partition.
I assumed the /boot partition was (hd0,2) because when I boot Ubuntu it says "Boot from (hd0,2) ext3" (My Ubuntu partition is ext4 formatted).

Here's my menu.lst, it's been customized:
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
default		1

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

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a5655211-67a0-40b6-83d0-1d5fe4c4102c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1558fe7d-cfe9-4ea4-8e6b-ca4fd08cfc3c

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

splashimage=(hd0,2)/boot/grub/breeze.xpm.gz

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		 -= OPERATING SYSTEMS =-
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

title		Ubuntu 9.04
uuid		1558fe7d-cfe9-4ea4-8e6b-ca4fd08cfc3c
kernel		/vmlinuz-2.6.28-11-generic root=UUID=a5655211-67a0-40b6-83d0-1d5fe4c4102c ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		.
root

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		 -= UBUNTU ADVANCED OPTIONS =-
root

title		Ubuntu 9.04 (Verbose Boot)
uuid		1558fe7d-cfe9-4ea4-8e6b-ca4fd08cfc3c
kernel		/vmlinuz-2.6.28-11-generic root=UUID=a5655211-67a0-40b6-83d0-1d5fe4c4102c ro 
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04 (Recovery Mode)
uuid		1558fe7d-cfe9-4ea4-8e6b-ca4fd08cfc3c
kernel		/vmlinuz-2.6.28-11-generic root=UUID=a5655211-67a0-40b6-83d0-1d5fe4c4102c ro  single
initrd		/initrd.img-2.6.28-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		.
root

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		 -= SYSTEM OPTIONS =-
root

title		Memory Diagnostic (memtest86+)
uuid		1558fe7d-cfe9-4ea4-8e6b-ca4fd08cfc3c
kernel		/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Boot from Floppy Disk
pause           Insert Floppy and press any key to boot.
chainloader	(fd0)+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Boot from CD
pause           Insert disk, remove any floppies, and press any key.
reboot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Reboot system
reboot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Shutdown system
halt

```

---

### Post by solidsnake204 on 2009-06-07
I hope bumping isn't against the rules...

---

### Post by solidsnake204 on 2009-06-07
I've tried (hd0,1) and (hd0,0) but still doesn't work.
I also changed the permissions so everyone can read/write to the file, but it still doesn't work.

I've searched around but haven't found anything relating to my problem.

---

### Post by sim909 on 2009-09-18
Are you sure you are trying the right partitions?
Try

mount

it will give all mounted devices, look for /boot, it should say something like /dev/sdaX. Remeber to subtract 1, i.e. if it says /dev/sda5 then your splash command needs to be 

splashimage=(hd0,4)/boot/grub/breeze.xpm.gz

Ah, just as I am writing I realize what your real problem might be: you need to take out "/boot". Again, if your grub partition is sda5, your command would be

splashimage=(hd0,4)/grub/breeze.xpm.gz

This is because (I think) within ubuntu your grub partition is mounted under /boot, but the reality is that the files are at the root of the partition. Just look at the "kernel" and "initrd" instructions in your menu/lst: they all point to /, not /boot/... Same goes with splashimage

Hope it helps

---

