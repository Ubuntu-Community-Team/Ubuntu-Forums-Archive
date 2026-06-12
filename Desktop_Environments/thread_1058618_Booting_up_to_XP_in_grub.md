---
title: "Booting up to XP in grub"
date: 2009-02-03
forum: Desktop Environments
---

### Post by DeltaFee on 2009-02-03
Hi,
 I have an xp installation on my harddrive and I use to dual boot. But, I lost that boot option on an accidental erase. 
here is my Fstab
> 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5140    41287018+   7  HPFS/NTFS
/dev/sda2            5141        9705    36668362+  83  Linux
/dev/sda3            9706        9729      192780   82  Linux swap / Solaris


heres my menu.lst:
> 
gfxmenu /boot/messages.blue

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
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,1)/boot/grub/splashimages/68224-tux_splash.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
password topsecret

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
# kopt=root=UUID=0b224239-ac94-4721-99f8-46a7e4bb2fcc ro

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

## ## End Default Options ##

title		Ubuntu 8.04
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0b224239-ac94-4721-99f8-46a7e4bb2fcc ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
boot

#title		Microsoft XP Pro
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0b224239-ac94-4721-99f8-46a7e4bb2fcc ro single
#initrd		/boot/initrd.img-2.6.24-23-generic
#boot

title		Ubuntu 8.04(recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0b224239-ac94-4721-99f8-46a7e4bb2fcc ro single
initrd		/boot/initrd.img-2.6.24-23-generic
boot

title		memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


Thanks

---

### Post by caljohnsmith on 2009-02-03
How about after the last line in your menu.lst:
```

### END DEBIAN AUTOMAGIC KERNELS LIST 
```
Put the following Windows entry:
```
title Windows
root (hd0,0)
chainloader +1
```
Let me know if that works or not.

---

### Post by jacksaff on 2009-02-03
The xp entry in your menu.lst is commented out (has # before it). This means it will be ignored when menu.lst is read by grub. Assuming nothing has changed with your xp install, removing the # in front of all the xp lines at the bottom of your menu.list should fix things.

---

### Post by DeltaFee on 2009-02-03
I tried it, but grub gave an error.

---

### Post by knny on 2009-02-03
Try using [Super Grub Disk]("http://www.supergrubdisk.org/") if you don't get farther. I always made positive experiences with SGD.

---

### Post by DeltaFee on 2009-02-04
Well I found out that my xp is corrupted, apparently I did something while installing ubuntu. which explains why I can't mount it either. Thanks again for the help.

---

