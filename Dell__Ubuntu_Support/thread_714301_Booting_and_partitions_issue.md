---
title: "Booting and partitions issue"
date: 2008-03-03
forum: Dell  Ubuntu Support
---

### Post by Canux08 on 2008-03-03
Machine: Dell Latitude D610
OSes: Windows XP SP2, Ubuntu 7.10. 
Clean install. 

After selecting Ubuntu from the OS menu at start-up, the first two lines of Linux start up appear followed by a blank screen. 

The machine then pauses for two to three minutes before continuing to boot.

By pressing CRTL+ALT+F1 I can skip the delay. 

Once I press CRTL+ALT+F1, see the start-up commands flowing, one of which indicates the machine was looking for resume partition. 

Is there a way for me to eliminate this boot delay?

---

### Post by logos34 on 2008-03-03
the resume partition is your swap.  Does swap mount?

Post your

sudo fdisk -l

and

cat /boot/grub/menu.lst

---

### Post by Canux08 on 2008-03-05
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        2339    18723757+   7  HPFS/NTFS
/dev/sda3            2340        4753    19390455   83  Linux
/dev/sda4            4754        4864      891607+   5  Extended
/dev/sda5            4754        4864      891576   82  Linux swap / Solaris

and 

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=eefe0920-9890-406b-bdb7-60a9efdea425 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=eefe0920-9890-406b-bdb7-60a9efdea425 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Dell Utility Partition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by logos34 on 2008-03-05
You didn't post the whole menu.lst.  There's a line near the top called 'timeout'.  It may be set too long.  If necessary lower it to 10 secs or less.  

I thought when you mentioned 'resume' there was a kernel option for swap (I have one), but I guess not.  You could take out the 'quiet' though--it might show more info on what's stalling it.

Check Gparted to make sure swap sda5 is mounting.  If not maybe the UUID has changed (stuff happens).   If it's not mounting, do

sudo swapon -a

Verify the UUID matches that in /etc/fstab:

blkid 

or

ls -l /dev/disk/by-uuid

---

### Post by Canux08 on 2008-03-05
here's the complete readout:

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
# kopt=root=UUID=eefe0920-9890-406b-bdb7-60a9efdea425 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=eefe0920-9890-406b-bdb7-60a9efdea425 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=eefe0920-9890-406b-bdb7-60a9efdea425 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Dell Utility Partition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by logos34 on 2008-03-05
Ok, so timeout is not the issue.

Run those UUID commands I posted above and check them against your /etc/fstab for swap.  Maybe that's the problem.  

As I said before, 'resume' message seems to be related to the swap or hibernation issue. Maybe someone else has some ideas.

---

### Post by Canux08 on 2008-03-12
> **logos34 said:**
> Ok, so timeout is not the issue.

Run those UUID commands I posted above and check them against your /etc/fstab for swap.  Maybe that's the problem.  

As I said before, 'resume' message seems to be related to the swap or hibernation issue. Maybe someone else has some ideas.

Here's what I get with blkid:
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0A05" TYPE="vfat" 
/dev/sda2: UUID="A45082E55082BD94" TYPE="ntfs" 
/dev/sda3: UUID="eefe0920-9890-406b-bdb7-60a9efdea425" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="4d569ee8-5f49-4ea9-ac51-20da428ee095" TYPE="swap" 

Here's the fstab file contents:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=eefe0920-9890-406b-bdb7-60a9efdea425 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4d569ee8-5f49-4ea9-ac51-20da428ee095 none            swap    sw              0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

