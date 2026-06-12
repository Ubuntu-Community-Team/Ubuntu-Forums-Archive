---
title: "Making GRUB Auto Select Ubuntu to boot"
date: 2009-03-05
forum: General Help
---

### Post by Ravernomina on 2009-03-05
HI... I have a computer with a recovery conceal and grub lets me choose to boot into it. But the thing is i wana go directly into ubuntu, can some 1 tell me how to make GRUB Boot Into Ubuntu on start up

TYVM!!!

     Ravernomina

---

### Post by Ravernomina on 2009-03-05
Bump

---

### Post by lykwydchykyn on 2009-03-05
can you post your /boot/grub/menu.lst file?

---

### Post by DeMus on 2009-03-05
> **Ravernomina said:**
> HI... I have a computer with a recovery conceal and grub lets me choose to boot into it. But the thing is i wana go directly into ubuntu, can some 1 tell me how to make GRUB Boot Into Ubuntu on start up

TYVM!!!

     Ravernomina

Open, with a text-editor, the file: /boot/grub/menu.lst
When you start reading it you find at the top some lines which say:

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
**default		0**

(line starting with # are text or comment lines)
The line you are looking for is the line: default       0
At the bottom of the file you see the listing of the bootable items you have in your computer. When the normal boot is, for example, the second item in the list, change the line: default  0 into default 1. (Alway 1 less than the number it has in the list, since grub starts counting at 0)

If you want to boot up fast you can also change: 
timeout		10
into
timeout		3
which gives you still time to press a key to choose another option.

---

### Post by Ravernomina on 2009-03-05
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
# kopt=root=UUID=5893d6e2-3c87-4145-8888-0d7a9ddad8d1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5893d6e2-3c87-4145-8888-0d7a9ddad8d1

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
uuid		5893d6e2-3c87-4145-8888-0d7a9ddad8d1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5893d6e2-3c87-4145-8888-0d7a9ddad8d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5893d6e2-3c87-4145-8888-0d7a9ddad8d1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5893d6e2-3c87-4145-8888-0d7a9ddad8d1 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5893d6e2-3c87-4145-8888-0d7a9ddad8d1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5893d6e2-3c87-4145-8888-0d7a9ddad8d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5893d6e2-3c87-4145-8888-0d7a9ddad8d1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5893d6e2-3c87-4145-8888-0d7a9ddad8d1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5893d6e2-3c87-4145-8888-0d7a9ddad8d1
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

---

