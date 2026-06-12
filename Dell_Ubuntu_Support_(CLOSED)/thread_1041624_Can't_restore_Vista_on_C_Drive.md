---
title: "Can't restore Vista on C Drive"
date: 2009-01-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by OceanView on 2009-01-16
I have a Dell Dimension E520.
I recently installed Ubuntu on the C drive with it's own partition.
I need to reformat and reinstall the Vista partition.
I use to be able to do this very easily by pressing F8 at bootup but I can't do that anymore. Is there a way I can do this again?
Will uninstalling Ubuntu restore everything back?

Any help would be appreciated.

---

### Post by theozzlives on 2009-01-16
You want evertything back? Without Ubuntu?

---

### Post by OceanView on 2009-01-16
> **theozzlives said:**
> You want evertything back? Without Ubuntu?

No, I want to keep Ubuntu.
But if I have to uninstall it, I will.

I tend to restore my Vista OS often which was easy before I installed Ubuntu but now I can't.
Maybe there is an easy way to do this again?

---

### Post by theozzlives on 2009-01-16
you may have inadvertantly deleted the recovery partition on your hard drive. Do you have a recovery CD?

---

### Post by OceanView on 2009-01-16
Yes I do. But I have never used it before as I really like the built in restore function.
Also, I didn't delete anything.
If something got deleted, it was from the Ubuntu installation.

---

### Post by pastalavista on 2009-01-16
More information is needed to help you. Are you in Ubuntu now? If you are, please copy and post the contents of /etc/fstab and also /boot/grub/menu.lst

---

### Post by OceanView on 2009-01-16
OK, Here is fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c7cf54d0-57a1-4425-9ea5-4689bda02fde /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=087668d0-ccf0-4ff5-86f6-8b84b4fdac85 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by OceanView on 2009-01-16
Menu.lst




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
# kopt=root=UUID=c7cf54d0-57a1-4425-9ea5-4689bda02fde ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c7cf54d0-57a1-4425-9ea5-4689bda02fde

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		c7cf54d0-57a1-4425-9ea5-4689bda02fde
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c7cf54d0-57a1-4425-9ea5-4689bda02fde ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		c7cf54d0-57a1-4425-9ea5-4689bda02fde
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c7cf54d0-57a1-4425-9ea5-4689bda02fde ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c7cf54d0-57a1-4425-9ea5-4689bda02fde
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c7cf54d0-57a1-4425-9ea5-4689bda02fde ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c7cf54d0-57a1-4425-9ea5-4689bda02fde
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c7cf54d0-57a1-4425-9ea5-4689bda02fde ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c7cf54d0-57a1-4425-9ea5-4689bda02fde
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by OceanView on 2009-01-16
> **theozzlives said:**
> you may have inadvertantly deleted the recovery partition on your hard drive. Do you have a recovery CD?


The recovery partition is still there (D drive)
I tried to install from the Restore CD's but it won't work for some reason.

Very Frustrating,

---

### Post by pastalavista on 2009-01-16
OK, have you tried booting the Dell Utility Partition? It is probably the restore function you were used to. After you do restore, you'll lose grub and the ability to boot Ubuntu so you'll have to re-install grub by booting from an Ububtu live install CD or you can download, burn and boot from a [supergrub]("http://www.supergrubdisk.org/") disk and fix it the easy way.

---

### Post by OceanView on 2009-01-16
> **pastalavista said:**
> OK, have you tried booting the Dell Utility Partition? It is probably the restore function you were used to. After you do restore, you'll lose grub and the ability to boot Ubuntu so you'll have to re-install grub by booting from an Ububtu live install CD or you can download, burn and boot from a [supergrub]("http://www.supergrubdisk.org/") disk and fix it the easy way.

Yes I did try but there are problems.
I can only get in from Vista file manager or Ubuntu file browser.
The problem is that I can't run the files from either places.
I need to get to a dos prompt and run it from there but can't seem to get to it.
The Dell utility option seems to be going nowhere when I select it.
It loads but just hangs there no matter how long I wait.

---

### Post by OceanView on 2009-01-16
What if I was to uninstall Ubuntu?

---

