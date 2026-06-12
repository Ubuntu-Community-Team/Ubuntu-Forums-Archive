---
title: "Windows + Dual Boot Problems"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Cover Slide on 2006-10-07
OK here's my story. first, I have two physical hard drives on my computer: my primary is 80 gb, while the secondary is 40 gb. I had been running windows on my primary for a while now. Originally, i had installed gentoo on the secondary, with the grub bootloader (which i can't remember if i installed on the mbr or not). But not liking it as much as ubuntu, which i had on my laptop, i replaced it with ubuntu. well that seemed to be a mistake. it seems when the grub started, if i chose windows, the gentoo bootloader would start, and if i chose windows from the gentoo screen, nothing would load. it would just stop at that screen with nothing happening at all. so then i tried to do fixmbr which got rid of grub, and the gentoo grub, but windows still wouldn't boot. well anyways, i ended up installing ubuntu on my secondary drive, which sees windows in the grub, but selecting it still gives me the blank screen. 

what i would like to do is make my windows usable again, hopefully without altering much, because i don't want to go through the hassle of installing all my programs again. I know the files are still intact, i can see and read them from ubuntu if i install ntfs support, so i'm guessing it's something small that windows needs and isn't seeing. I would rather fix that something small than have to install everything all over again. Any suggestions?

---

### Post by confused57 on 2006-10-07
Here's a thread with a similar problem as yours:
[http://www.ubuntuforums.org/showthread.php?t=272759](http://www.ubuntuforums.org/showthread.php?t=272759)

May give you some ideas...

---

### Post by aysiu on 2006-10-07
I don't know how to solve your problem, but I know what you should do to help others solve your problem:

Post the output of these commands: ```
sudo fdisk -l
cat /boot/grub/menu.lst
``` By the way, you don't have to install NTFS support to see and read NTFS in Ubuntu.

---

### Post by Cover Slide on 2006-10-07
sudo fdisk -l
> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78147688+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4664    37463548+  83  Linux
/dev/hdb2            4665        4865     1614532+   5  Extended
/dev/hdb5            4665        4865     1614501   82  Linux swap / Solaris

cat /boot/grub/menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu, kernel 2.6.15-27-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1



---

### Post by confused57 on 2006-10-07
In your Windows entry, you could try:

rootnoverify (hd0,0)

instead of:
root (hd0,0)

---

