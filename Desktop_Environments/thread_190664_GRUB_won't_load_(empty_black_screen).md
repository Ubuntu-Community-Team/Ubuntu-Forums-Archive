---
title: "GRUB won't load (empty black screen)"
date: 2006-06-06
forum: Desktop Environments
---

### Post by saepia on 2006-06-06
Hi,

I've got Fujitsu-Siemens Amilo Pro V2030 notebook. I've got HDD partitioned in following way:

/dev/sda1 (boot) primary ntfs 9gb
/dev/sda2 primary reiserfs3.6 9gb
/dev/sda5 logical swap 1gb
/dev/sda6 log vfat 40gb

I installed Windows XP on /dev/sda1, as a second OS because I need to use my scanner (there are no drivers for linux). After installation, I've booted my computer using gentoo install cd (this is only linux CD which i currently have, and which gives me access to the console). I did:

```

mount /dev/sda2 /mnt/gentoo
chroot /mnt/gentoo /bin/bash

```

to achieve access to my ubuntu. I modified /boot/grub/menu.lst:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-23-686
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

title		x
rootnoverify	(hd0,0)
makeactive
chainloader	+1


### END DEBIAN AUTOMAGIC KERNELS LIST

```

and then I did:

```

grub

```

in grub:

```

root (hd0,1)
setup (hd0)

```

and after reboot, when computer should display GRUB menu or do anything, there are only black screen. I've did similar operation on Ubuntu 5.10 (I'm using 6.06 now) and it was working without any problems. I am experienced linux user, I've installed dual OS computer many times but I've never seen something like that. I tried to comment out last (windows) entry but it don't solve the problem.

Thanks in advance,

---

