---
title: "Need help editing menu.lst"
date: 2006-06-16
forum: Desktop Environments
---

### Post by frup on 2006-06-16
I have 3 ATA Hard drives.
Primary Master (hda) is Ubuntu
Primary Slave (hdb) is Linspire
Secondary Master is DVD
Secondary Slave (hdd) is ext3

I can not load linspire. i dont really care but would like to know how to fix it.
i have edited menu.lst for both ubuntu and linspire and i cant seem to fix the problem... i am getting no error messages.

Ubuntu's menu.lst > i edited linspires part to hdb1 from hda ... before this it used to show the splash and then go to ubuntus log in screen... now with my edits of the two menu.lst files it stalls on linspires splash... ubuntu still works fine.
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
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.15-23-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-k7
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Linspire 5.0.59 on /dev/hdb1 (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hdb1 rootdev=0x0301 ramdisk=32000 vga=0x311 splash=silent video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hdb1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Redetect (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hda1 rootdev=0x0301 ramdisk=32000 noresume2 redetect video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Diagnostics (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10 root=/dev/hda1 rootdev=0x0301 ramdisk=32000 noresume2 single splash=0 Diagnostics video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hda1:0x8800@4096 
initrd		/boot/initrd-2.6.10.gz
savedefault
boot
```

Linspires menu.lst > note places where it says hdb/hd1 used to say hda
```
# Generated by jiffyboot version 7.0.53. If this file is edited, the
# system will stop modifying it.  To allow the system to resume
# management of this file, remove it and run /sbin/jiffyboot

default=0
timeout=10
color cyan/green magenta/green
splashimage=/boot/grub/bootsplash.xpm.gz

title Linspire 5.0.59 on /dev/hdb1
root (hd1,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hdb1 rootdev=0x0301  ramdisk=32000 vga=0x311 splash=silent video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hdb1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)

title Redetect
root (hd1,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hdb1 rootdev=0x0301  ramdisk=32000 noresume2 redetect video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hdb1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)

title Diagnostics
root (hd1,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hdb1 rootdev=0x0301  ramdisk=32000 noresume2 single splash=0 Diagnostics video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hdb1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)

title Redetect
root (hd1,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hdb1 rootdev=0x0301  ramdisk=32000 noresume2 redetect video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hdb1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)

title Diagnostics
root (hd1,0)
kernel /boot/vmlinuz-2.6.10  root=/dev/hdb1 rootdev=0x0301  ramdisk=32000 noresume2 single splash=0 Diagnostics video=vesafb:nomtrr video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2=swap:/dev/hdb1:0x8800@4096
initrd /boot/initrd-2.6.10.gz
# (Boot priority: 102, mounted at /)
```

---

### Post by weijie90 on 2006-06-16
hmm... i wonder whether its a matter of the linspire kernel in /boot.

where is /boot? do you have two /boot-s?

---

### Post by frup on 2006-06-16
i have them both on two seperate drives..

so there is hda1/boot 
and hdb1/boot

---

### Post by frup on 2006-06-16
should i just format the linspire drive?

i was sort of hoping to use that drive as a tester for different systems...
currently i have tried mandrake linspire and ubuntu

---

### Post by frup on 2006-06-16
ok i'll just format

---

### Post by frup on 2006-06-16
hmm once last try for help

---

### Post by Herman on 2006-06-16
Wouild you be interested in learning how to use GRUB to find your Linspire kernel with GRUB's Command Line Interface? it's really not very difficult. I think it will solve your problem. [*Click Here.*]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
In the meantime, I'm getting sleepy right now, but I'll check your posted info and see if I can help at all. 
Regards, Herman :D

Edit: I checked your menu.lsts, but I'm afraid I'm just too tired  right now to make much sense out of them and/or I would need the output of sudo fdisk -lu so I can see what's where to help me  to help you. 
```
sudo fdisk -lu
```

---

