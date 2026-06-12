---
title: "grub error after 7.10 upgrade (e1505n)"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by icorey on 2007-10-23
I upgraded to ubuntu 7.10 last night on my dell e1505n (came with ubuntu 7.04 preinstalled).  **After the upgrade, everytime i boot up the laptop i get "Error 15: File not Found   Press any key to continue..." after grub tries to boot up.**  any kernel i try to boot yields the same error.

i can boot the laptop via the command line on grub with the following commands:
```
root (hd0,2)
kernel /vmlinuz-2.6.22-14-generic root=/dev/sda6
initrd /initrd.img-2.6.22-14-generic
boot
```

i tried changing a few things in the menu.lst file but nothing has worked and my inexperience with grub kinda limits me with what i can change.

Here's what fdisk -lu returns:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2          112455     4321484     2104515    b  W95 FAT32
/dev/sda3   *     4321485     4723109      200812+  83  Linux
/dev/sda4         4723110   234436544   114856717+   f  W95 Ext'd (LBA)
/dev/sda5         4723173     7325639     1301233+  82  Linux swap / Solaris
/dev/sda6         7325703   234436544   113555421   83  Linux

```

And here's what's in the menu.lst file:
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5525b2b6-f42e-4e7b-be6c-5bd48c59a92a ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5525b2b6-f42e-4e7b-be6c-5bd48c59a92a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5525b2b6-f42e-4e7b-be6c-5bd48c59a92a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5525b2b6-f42e-4e7b-be6c-5bd48c59a92a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5525b2b6-f42e-4e7b-be6c-5bd48c59a92a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        kernel /vmlinuz debug boot=dellfactory quiet
        initrd /initrd.gz

```

Let me know if any other info's needed.

---

### Post by stevanbt on 2007-10-23
Hi,
I'm not sure how much help this will be but I have a Dell (Optiplex 320) and I couldn't get it to boot 7.04 using Grub, so I used LILO instead (there was a thread on this forum but I can't find it now).  Since then I've successfully upgraded to 7.10.

So it might be worth looking for advice on installing LILO instead of Grub.

Thanks, Steve.

---

### Post by meierfra on 2007-10-23
You need to remove all the "/boot"'s:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=5525b2b6-f42e-4e7b-be6c-5bd48c59a92a ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

---

