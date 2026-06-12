---
title: "I've got a really screwed up MBR, please help fix"
date: 2006-06-17
forum: Desktop Environments
---

### Post by derrick1985 on 2006-06-17
Hi,

I am having a huge problem with Ubuntu ever since I installed it. I had PCLinuxOS (which uses lilo) installed on an IDE hard drive (second ide, primary) on my computer and the bootloader installed to the MBR of my SATA drive which is set to first boot. I installed Ubuntu to my SATA drive in a new partition and grub automatically was supposed to install to the MBR of the SATA drive. It didn't, and lilo continued to load. I was able to set up so that lilo could load up ubuntu, but after I did an update, the kernel changed and I couldn't boot it again. So, I decided to boot the older kernel and install grub to the MBR. That part worked, but the default config was all messed up. It would not load any of my three os's. I was finally able to boot into Ubuntu, but now can't figure out how to get into anything else. Here is a copy of my MBR.

MBR

[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-25-386
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2)
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd5.
title		pclinuxos (on /dev/hdd5)
root		(hd1)
kernel		/boot/vmlinuz-2.6.12-oci6.mdk-i586-up-1GB root=/dev/hdd5 ro noapic nolapic nomce acpi=ht psmouse.proto=imps splash=silent 
initrd		/boot/initrd-2.6.12-oci6.mdk-i586-up-1GB.img
savedefault
boot
[/PHP]

and my device.map

(hd0)	/dev/hdc
(hd1)	/dev/hdd
(hd2)	/dev/sda

CAn anybody help me get on the right track?

Thanks

Derrick

---

### Post by Sef on 2006-06-17
Try this:

[http://www.ultimatebootcd.com/index.html]("http://www.ultimatebootcd.com/index.html")

or this:

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by derrick1985 on 2006-06-19
You mean there is no way to fix this from a terminal?

---

### Post by Gustav on 2006-06-19
Your menu.lst looks quite strange. (it's not you mbr, the mbr is something else)

Try running 'sudo grub-update'

It might work.

---

### Post by derrick1985 on 2006-06-19
[QUOTE=Gustav]Your menu.lst looks quite strange. (it's not you mbr, the mbr is something else)

Try running 'sudo grub-update'

It might work.[/QUOTE]

Command not found.

---

### Post by Gustav on 2006-06-19
[QUOTE=derrick1985]Command not found.[/QUOTE]
Sorry, the command might be wrong, but I think it was something like that (I'm not on by ubuntu box at the moment)

Maybe it is update-grub instead? Try that :).

---

### Post by Gustav on 2006-06-19
And if that doesn't work, you can look at this thread: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

