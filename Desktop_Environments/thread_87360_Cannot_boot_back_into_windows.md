---
title: "Cannot boot back into windows"
date: 2005-11-07
forum: Desktop Environments
---

### Post by sfpiano on 2005-11-07
I have windows installed on my second hard drive (it was listed as sdb in the installer), and have ubuntu installed on a seperate partition of my first (sda) hard drive). I installed grub to my second hard drive( hd1 ) and can boot into ubuntu, but not windows. The error I get is:

root(hd1, 0)
Filesystem type unknown, partition type 0xf

savedefault
map(hd0) (hd1)
map(hd1) (hd0)
chainloader +1

---

### Post by Ampersand on 2005-11-08
Could you post the contents of your /boot/grub/menu.lst here?

---

### Post by mcduck on 2005-11-08
It might also help if you go to BIOS and set the Windows-HD's mode to LBA or Large.. (I got exactly the same error after installing Ubuntu, and that fixed it.)

---

### Post by sfpiano on 2005-11-08
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP
root		(hd0,0)
savedefault
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader	+1


```


Here's my fdisk output, I don't know if it helps or not.
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       11606    93217162+   f  W95 Ext'd (LBA)
/dev/sda2   *       11607       14593    23993077+  83  Linux
/dev/sda5               2       11475    92164873+   7  HPFS/NTFS
/dev/sda6           11476       11606     1052226   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS

```


My windows partition is the sdb1 one byitself. The other ntfs partition is just for storage.

---

### Post by sfpiano on 2005-11-08
[QUOTE=mcduck]It might also help if you go to BIOS and set the Windows-HD's mode to LBA or Large.. (I got exactly the same error after installing Ubuntu, and that fixed it.)[/QUOTE]


Tried that with both hard drives and it didn't work.

---

### Post by sfpiano on 2005-11-08
Ok, I had to wipe Umbuntu b/c I couldn't get back into windows so I want ot make sure I do this correctly this time. I have two SATA hard drives; one complete ntfs on which windows is installed, and the other has a blank ntfs partition, and the second part of it will be used for linux. The on where windows is installed is actually the second hard drive; the blank one is the first one because that's where windows used to be before I wiped my old copy. When I go to install grub and it asks me if I should install it to the mbr of the first hard drive or whatever, should I say yes, or do I have to manuallly do something?

*Note - when I switched my hdd boot up to be 'Large', windows wouldn't boot at all; it just loaded up a blank screen, so I had to switch it back to auto.

---

