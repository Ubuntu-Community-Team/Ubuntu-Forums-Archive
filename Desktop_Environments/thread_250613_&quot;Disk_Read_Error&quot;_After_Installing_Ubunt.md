---
title: "&quot;Disk Read Error&quot; After Installing Ubuntu"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Orbit45244 on 2006-09-04
So yesterday I installed Ubuntu along with my Windows XP partition.  I manually repartitioned my Windows partition, using GParted, taking 10 GB off of it.  But now when I try to access my Windows partition (I've tried it in GRUB and GAG) I get the error:
> A disk read error has occured.
And I get the same error when trying to boot up Ubuntu using GAG.  But, when using GParted on the LiveCD, it says that I still have my Windows Partition and that it's an NTFS filesystem.  Someone please help!  I really want to be able to access Ubuntu and Windows!

---

### Post by bernied on 2006-09-04
So you can use ubuntu booting through grub, right?
Can you post the results of the following commands (in a terminal):
```
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by iONiK on 2006-09-04
All those who have had the error probably have never used Linux because they couldn't install right, therefore, not many people would be able to help you with this one... UNLESS...

I can... My advice is to buy a new hard drive.

-not.

---

### Post by Orbit45244 on 2006-09-04
The output of cat /boot/grub/menu.lst is:

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
# kopt=root=/dev/hda2 ro

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

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

The output of sudo fdisk -l is:
```
Password:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8458    67938853+   7  HPFS/NTFS
/dev/hda2            8459        9676     9783585   83  Linux
/dev/hda3            9677        9733      457852+   5  Extended
/dev/hda5            9677        9733      457821   82  Linux swap / Solaris
:

```

---

### Post by bernied on 2006-09-04
That entry for windows looks right to me. The only thing I can think of to try is to change

root (hd0,0)
to 
rootnoverify (hd0,0)

If this doesn't work you could suspect that you've damaged your windows install when resizing that partition. You could check this with a windows recovery cd, however this is likely to want to re-write your master boot record, so you woulnd't be able to boot your ubuntu install. You could make a boot floppy using grub-floppy first, in case you end up with neither system. Try putting a blank formatted floppy into the drive and (in a terminal):
sudo grub-floppy /dev/fd0

Then check that this works - can you reboot from the floppy? (leave the floppy in the drive and reboot) - before you do anything else drastic.

---

