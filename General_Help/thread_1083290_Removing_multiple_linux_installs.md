---
title: "Removing multiple linux installs"
date: 2009-02-28
forum: General Help
---

### Post by farfromapro on 2009-02-28
I installed a few different versions of linux to play around with.  I want to keep just my 8.10 ubuntu.  
When grub loads I have 3 OS's that I can boot to (all some form of linux).  What is the best way to remove all the OS's I don't want?
My original thought was to use fdisk or parted and delete the partions where each OS resideds... I can't figure out where each OS actually exists so I don't know what I can delete....

I may attempt to load each OS and remove each OS from it's respective self.....

my menu.lst file in the /boot/grub dir is as follows:  I think all the installs are on the same partition...




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
# kopt=root=UUID=a11dd9bb-b36c-4bdc-8c09-25c181802562 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a11dd9bb-b36c-4bdc-8c09-25c181802562

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		a11dd9bb-b36c-4bdc-8c09-25c181802562
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a11dd9bb-b36c-4bdc-8c09-25c181802562 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a11dd9bb-b36c-4bdc-8c09-25c181802562
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a11dd9bb-b36c-4bdc-8c09-25c181802562 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a11dd9bb-b36c-4bdc-8c09-25c181802562
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a11dd9bb-b36c-4bdc-8c09-25c181802562 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a11dd9bb-b36c-4bdc-8c09-25c181802562
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a11dd9bb-b36c-4bdc-8c09-25c181802562 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a11dd9bb-b36c-4bdc-8c09-25c181802562
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-server (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-server root=UUID=5b540169-4dcb-4dd5-82a4-8f09e67169f3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-server (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-server root=UUID=5b540169-4dcb-4dd5-82a4-8f09e67169f3 ro single 
initrd		/boot/initrd.img-2.6.27-7-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


Any thoughts?

Once I'm down to 1 OS will GRUB still load?  If so how can I stop that from happening?

Thanks!

---

### Post by dcstar on 2009-02-28
> **farfromapro said:**
> I installed a few different versions of linux to play around with.  I want to keep just my 8.10 ubuntu.  
When grub loads I have 3 OS's that I can boot to (all some form of linux).  What is the best way to remove all the OS's I don't want?
My original thought was to use fdisk or parted and delete the partions where each OS resideds... **I can't figure out where each OS actually exists** so I don't know what I can delete....
........


```
ls -al /dev/disk/by-uuid
```

---

### Post by farfromapro on 2009-03-01
```
~$ ls -al /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 120 2009-03-01 11:07 .
drwxr-xr-x 5 root root 100 2009-03-01 11:07 ..
lrwxrwxrwx 1 root root  10 2009-03-01 11:07 46ea4f8b-6ee4-495c-9188-a0d756469bac -> ../../sdb5
lrwxrwxrwx 1 root root  10 2009-03-01 11:07 5b540169-4dcb-4dd5-82a4-8f09e67169f3 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2009-03-01 11:07 a11dd9bb-b36c-4bdc-8c09-25c181802562 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-03-01 11:07 d4f9734f-5607-40a4-ae25-efa43e4f0d83 -> ../../sda5

```

Now I see I have installs on sda1, sda5, sdb1, sdb5

Based on my earlier grub menu the uuid for my "keeper" is a11dd9bb-b36c-4bdc-8c09-25c181802562 which matches the install on sda1... So I can remove all partitions other than sda1 and I should be down to one OS!

Hopefully I do it right!


Thanks for the direction.  I appreciate the help!

---

### Post by farfromapro on 2009-03-01
Removing the partition with my server on it was easy... but these two seem to share the same partition? 

the uudi is the same.
One I updated and one I didn't.

I want to keep the most current 2.6.27-11.... not the -7

From the menu.lst and the ls command posted above it appears they share the same partition.... So does that mean I just find the -7 kernel and remove it?


title Ubuntu 8.10, kernel 2.6.27-11-generic uuid a11dd9bb-b36c-4bdc-8c09-25c181802562

title Ubuntu 8.10, kernel 2.6.27-7-generic uuid a11dd9bb-b36c-4bdc-8c09-25c181802562

---

