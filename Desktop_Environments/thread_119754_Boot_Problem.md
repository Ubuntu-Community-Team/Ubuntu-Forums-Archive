---
title: "Boot Problem"
date: 2006-01-20
forum: Desktop Environments
---

### Post by mysticqas on 2006-01-20
Guys I have two hard disks 40GB each with 2 Partitions on each disk...Ist disk has two partitons both NTFS with Windows Installed on C and D for data..Second hard disk also has 1 NTFS partition and 1 Exts for linux and one swap....

I installed Linux on second drive by disconnecting 1st hard disk (because partitioner wasn't loading during installation)...but after successfully installing Ubutnu when I connected Windows drive the linux hangs just before booting where it says "Loading Modules"..

My linux disk jumer was set at Slave when I installed Linux and Windows disk as Master but I changed it to Master as I read somewhere in this forum that to boot dual set your ubuntu disk as master and windows as slave..I edited my menu.Ist as shown below to add windows in Grub loader..Now everytime I have to boot Ubuntu I have to set my Linux drive as slave because it doesn't work as Master and hangs where it says "Loading Modules"..Windows is working fine.

Please help me so that I can boot both os without setting jumpers again and again..here is my menu.ist

> <quote>
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot



### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
savedefault
makeactive
chainloader +1



thanks for the help:D

---

### Post by epostma on 2006-01-20
Couple questions:
1) If you boot windows, is that using GRUB or not?
2) How do you (try to) boot ubuntu? Using GRUB or using the windows boot thingy?

When looking at your menu.lst file, something is strange: GRUB says that the partition that ubuntu is on, is something else than what it tells the kernel.

Booting is a strange and wonderful process: first GRUB is loaded, then it is told where to find a kernel by the configuration file and/or by input from a user, then that kernel is loaded, with some parameters telling where to find the root of the filesystem where it's supposed to live.

In your file, grub is told to look for the kernel on the third partition of the **first** disk: root (hd0,2). (grub starts counting at 0). But it's ordered to tell that kernel that its filesystem is on the third partition of the **second** disk: kernel linux-blah root=hdb3 blahblah (linux starts counting at *a*, for disks, and at 1, for partitions). So I guess something goes wrong there. Although I would have expected an error message that is more logical. Anyway. You can try different combinations of:
* putting one hard drive as master, the other one as slave,
* telling grub to look at (hd0,2) or (hd1,2),
* telling grub to tell linux to look at hda3 or hdb3.

---

### Post by mysticqas on 2006-01-20
thanks for the reply epostma..
1. yes I'm using Grub to boot windows
2. using Grub

can you please tell me more about kernel?..what do you think my menu.ist should be like? I have already tried what you said with no success .

---

### Post by lha on 2006-01-20
Your linux isn't booting up because it can't find the files it needs. When you moved Ubuntu drive from hdb to hda, all references in your settings to hdb remained the same. Reinstallation will fix this, but I guess you don't want to do that...

So get yourself a Linux live-cd. A small typo in the files you need to edit may render Ubuntu unbootable, so you need a backup plan to restore original settings. [Knoppix]("http://knoppix.org/") is my favourite, even though it doesn't have Gnome. (You can boot from cds, right?)

Please post here the output of following commands:
```
cat /boot/grub/device.map
sudo fdisk -l
cat /etc/fstab
```

---

