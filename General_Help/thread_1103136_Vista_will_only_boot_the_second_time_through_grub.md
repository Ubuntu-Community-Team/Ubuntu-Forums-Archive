---
title: "Vista will only boot the second time through grub"
date: 2009-03-22
forum: General Help
---

### Post by vbman11 on 2009-03-22
Hi all!

So when my computer boots it shows the grub menu and when I select ubuntu it boot directly into ubuntu, but when I select vista it says "this is not a bootable partition...press any key to continue..." so i do and then it shows the menu again except this time when I select vista again it boots into vista with no errors. this just started recently with intrepid(8.10) and I've had the same setup since Gutsy(7.10). What i've been trying to figure out how to do lately is restore the mbr so I can just remove ubuntu altogether, only because my job needs lots of space on windows. so if there is a way to restore the mbr WITHOUT a windows cd or recovery disks, please tell me.

Thanks

btw here is my menu.lst:
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
# kopt=root=UUID=6c2e6509-1e79-414e-9fbe-c5ed58ed3e6f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6c2e6509-1e79-414e-9fbe-c5ed58ed3e6f

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

## ## End Default Options ###

This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (OS)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (Recovery)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

# This is a divider
title		Linux operating systems:
root

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6c2e6509-1e79-414e-9fbe-c5ed58ed3e6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6c2e6509-1e79-414e-9fbe-c5ed58ed3e6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6c2e6509-1e79-414e-9fbe-c5ed58ed3e6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6c2e6509-1e79-414e-9fbe-c5ed58ed3e6f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6c2e6509-1e79-414e-9fbe-c5ed58ed3e6f
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by meierfra. on 2009-03-22
> if there is a way to restore the mbr WITHOUT a windows cd or recovery disks, 

Yes. In a terminal in Ubuntu:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo lilo -A /dev/sda 1
```

This installs a Windows type MBR and sets the boot flag to the Vista partition. But I'm not sure that it will cure the  "this is not a bootable partition.." problem. That sounds more like a problem with your bios, rather than a grub problem.


After you do this, you won't be able to boot into Ubuntu anymore.
If  you still want to boot into Ubuntu, let me know and  I  show you how to add Ubuntu to the Vista boot loader.  (But that should be done before you run the above commands).

---

