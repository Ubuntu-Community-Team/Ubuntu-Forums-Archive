---
title: "[SOLVED] boot menu.lst error"
date: 2008-12-08
forum: General Help
---

### Post by abhilashm86 on 2008-12-08
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
# kopt=root=UUID=67b2988e-eb79-445f-a7b2-25c061008e56 ro root=/dev/hda1 ro noapic

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=67b2988e-eb79-445f-a7b2-25c061008e56 ro root=/dev/hda1 ro noapic quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=67b2988e-eb79-445f-a7b2-25c061008e56 ro root=/dev/hda1 ro noapic single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=67b2988e-eb79-445f-a7b2-25c061008e56 ro root=/dev/hda1 ro noapic quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=67b2988e-eb79-445f-a7b2-25c061008e56 ro root=/dev/hda1 ro noapic single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=67b2988e-eb79-445f-a7b2-25c061008e56 ro root=/dev/hda1 ro noapic quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=67b2988e-eb79-445f-a7b2-25c061008e56 ro root=/dev/hda1 ro noapic single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=67b2988e-eb79-445f-a7b2-25c061008e56 ro root=/dev/hda1 ro noapic quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=67b2988e-eb79-445f-a7b2-25c061008e56 ro root=/dev/hda1 ro noapic single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


what is error in this menu.lst,my ubuntu is not booting,it says loading please wait and does not boot even after 2 minutes ,so i booted from ubuntu live cd,then i opened my file system,this is copy of menu.lst,yesterday i installed some boot splash images,so i went wrong their i guess,please help

---

### Post by PocketDog on 2008-12-08
When the grub screen appears highlight the kernel you want to boot, and press E. Edit the kernel line to remove both 'quiet' and 'splash'. Press enter. Press B to boot up that kernel. Watch the boot entries, and you'll know which startup sequence or program is hanging on you. This will help us to help you a little more

---

### Post by plucky on 2008-12-08
> title Ubuntu 8.04.1, kernel 2.6.24-22-generic
[color=blue]root (hd0,7)[/color]
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=67b2988e-eb79-445f-a7b2-25c061008e56 ro [color=red]root=/dev/hda1 ro[/color] noapic quiet splash
initrd /boot/initrd.img-2.6.24-22-generic
quiet


Do you know which partition is your /root partition.There seems to be a conflict between the highlight in blue and the one in red.The blue one says your root partition is /dev/hda6 and the kernel line says it is /dev/hda1.

From the Live CD post output of ```
sudo blkid
sudo fdisk -l
``` that is Lowercase L not a 1

Also you need to edit the Default options in menu.lst to the correct values as those reflect what is in the kernel lines.


Good Luck

p.s This is already solved in another [url=http://ubuntuforums.org/showthread.php?t=1005167[thread[/url] (Double post)

---

### Post by abhilashm86 on 2008-12-08
> **plucky said:**
> Do you know which partition is your /root partition.There seems to be a conflict between the highlight in blue and the one in red.The blue one says your root partition is /dev/hda6 and the kernel line says it is /dev/hda1.

From the Live CD post output of ```
sudo blkid
sudo fdisk -l
``` that is Lowercase L not a 1

Also you need to edit the Default options in menu.lst to the correct values as those reflect what is in the kernel lines.


Good Luck
riends i downloaded grub menu.lst from internet and repaired thr GRUB menu.lst. So it was my mistake yesterday coz i had edited menu.lst for boot splash images,i ran ubuntu in older kernels there some command options came and i had option of repairing boot options, thanks GOD at the end i successfully repaired,i would have posted error but it was in command mode...........
thanks friends i did it,it was an adventure repairing it,i guess i wont touch or edit O.S codes unless i know evrything!!!!!!:p

---

### Post by abhilashm86 on 2008-12-08
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=67b2988e-eb79-445f-a7b2-25c061008e56 ro root=/dev/hda1 ro noapic

the last line was the error part,the default option from original menu.lst showed the mistake friends,thanks for support friends

---

### Post by PocketDog on 2008-12-08
Just for info, that last line wasn't the problem, that was commented out with a # and so was ignored at boot.

---

### Post by abhilashm86 on 2008-12-09
> **PocketDog said:**
> Just for info, that last line wasn't the problem, that was commented out with a # and so was ignored at boot.

yes i know,what i am telling i deleted those lastline along with quiet splash through out menu.lst,now ubuntu is booting normally!!!!!!

---

