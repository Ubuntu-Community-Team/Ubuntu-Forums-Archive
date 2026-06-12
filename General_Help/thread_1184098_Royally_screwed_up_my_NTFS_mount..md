---
title: "Royally screwed up my NTFS mount."
date: 2009-06-10
forum: General Help
---

### Post by Turbo Audi on 2009-06-10
I did something silly. I wanted my XP file system mounted on login, so I tried to do it but apparently I did it totally wrong. 

> DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

> libhal.c 1399: wrong reply from hald. expecting an array.

These are the errors I get. 

My fdisk looks like this:

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ed9092b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19445   156191931    7  HPFS/NTFS
/dev/sda2           19446       38913   156376710    5  Extended
/dev/sda5           19446       38118   149990841   83  Linux
/dev/sda6           38119       38913     6385806   82  Linux swap / Solaris


Any ideas how to reset it to the original settings?

---

### Post by synapsys on 2009-06-10
What exactly did you do to try and have the partition mount?

---

### Post by Turbo Audi on 2009-06-10
> **synapsys said:**
> What exactly did you do to try and have the partition mount?

I copied what I saw in /properties. :(

---

### Post by synapsys on 2009-06-10
To where? /boot/grub/menu.lst? 
If so... please post contents of that file

---

### Post by Turbo Audi on 2009-06-10
> **synapsys said:**
> To where? /boot/grub/menu.lst? 
If so... please post contents of that file

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
# kopt=root=UUID=7ad6440e-90e2-4aea-971c-0eec46c515d2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7ad6440e-90e2-4aea-971c-0eec46c515d2

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7ad6440e-90e2-4aea-971c-0eec46c515d2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7ad6440e-90e2-4aea-971c-0eec46c515d2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7ad6440e-90e2-4aea-971c-0eec46c515d2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7ad6440e-90e2-4aea-971c-0eec46c515d2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7ad6440e-90e2-4aea-971c-0eec46c515d2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by merlinus on 2009-06-10
Did you perhaps copy it to /etc/fstab?

Post that file so we can see.

---

### Post by Turbo Audi on 2009-06-10
> **merlinus said:**
> Did you perhaps copy it to /etc/fstab?

Post that file so we can see.

here it is....


> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7ad6440e-90e2-4aea-971c-0eec46c515d2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c81bcc55-9d48-4b5b-86b3-df712680dab3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by merlinus on 2009-06-10
Doesn't look like you screwed it up.  Can you access windows from the grub menu?

---

### Post by Turbo Audi on 2009-06-10
> **merlinus said:**
> Doesn't look like you screwed it up.  Can you access windows from the grub menu?

RESOLVED.

I installed NTFS Config Tool from Synaptic and remounted it from there.

[http://www.debrass.net/2009/05/23/ubuntu-ntfs-support-ntfs-3g/](http://www.debrass.net/2009/05/23/ubuntu-ntfs-support-ntfs-3g/)

Thanks merlinus and synapsys for your time.

---

### Post by merlinus on 2009-06-10
Well done!  That would have been my next suggestion.

---

