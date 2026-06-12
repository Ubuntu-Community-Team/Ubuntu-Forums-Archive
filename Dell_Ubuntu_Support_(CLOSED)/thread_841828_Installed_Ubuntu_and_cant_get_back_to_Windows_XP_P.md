---
title: "Installed Ubuntu and cant get back to Windows XP Partition"
date: 2008-06-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by panquake on 2008-06-26
So I installed Ubuntu on  20GB of an 80 GB HD with Windows XP still installed... at least I think it is. I can't find where to access it and if its gone I would like to free up the rest of the space left on the drive. Any clues on what I should do, I am pretty new to this. :guitar:

---

### Post by LeoSolaris on 2008-06-26
Alright, first thing, establish if Windows is still there.

Open Nautilus (your file manager in Ubuntu, you can get to it by going to Places on the taskbar, top left corner, and picking one. Home is the easiest.) and on the left hand side there should be a panel that lists quick links titled "Places". First one is your home folder, second your desktop, third (by default) should be your root directory where all of the under the hood stuff in Ubuntu lives.

The next one should be your windows partition. It should be unmounted by default. Clicking on it will mount it, then clicking again will take you to the lowest level of Windows file structure. If there is only you, your desktop, and your root partition, you may have overwritten your XP partition when you installed.

Another thing you can check is going to your terminal and entering ```
sudo gedit /boot/grub/menu.lst
```It will bring up the config file for grub, your boot loader. Scroll down it and at the end it should look like this: > ## ## End Default Options ##

title        Ubuntu 8.04
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=476ca36e-599d-4f02-a5bb-ae8e5bce9f2a ro quiet
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04 (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=476ca36e-599d-4f02-a5bb-ae8e5bce9f2a ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1If the last one is not there, but you can mount the windows partition in nautilus, then grub is ignoring windows for some reason. Just copy and paste the last two entries, the divider and the Windows (you can change the title line to what ever you like by the way)

---

### Post by panquake on 2008-06-28
yeah i must have over written it...
heres what came up...

so if i did overwrite it, how would i free up the other space and get rid of the partition? 



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
# kopt=root=UUID=27507c46-86d8-440e-abbb-f517f399a211 ro

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

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=27507c46-86d8-440e-abbb-f517f399a211 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=27507c46-86d8-440e-abbb-f517f399a211 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=27507c46-86d8-440e-abbb-f517f399a211 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=27507c46-86d8-440e-abbb-f517f399a211 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by logos34 on 2008-06-28
ubuntu didn't detect it and add it to menu.lst.

Double check with this command:

**sudo fdisk -l**

---

### Post by panquake on 2008-06-28
nevermind

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by logos34 on 2008-06-28
letter 'l', not number 1

in the future just copy 'n paste

---

### Post by panquake on 2008-06-28
nah i just had to reopen the terminal to get it to work, copy and pasting is the one thing i do know how to do here on ubuntu.

---

