---
title: "restoring GRUB after installing xp"
date: 2009-01-07
forum: General Help
---

### Post by civillian on 2009-01-07
I just reinstalled XP (for video editing on my computer) and I remembered that it would get rid of grub and replace it with its own bootloader.

I installed XP on a seperate hard drive, so now my hard drive config is like this:

/dev/sda1 --> XP
/dev/sdb1 --> Ubuntu 8.10
/dev/sdb2 --> Ubuntu 8.10 swap

I followed the howto here ([http://http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5]("http://http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5"))

and it didnt work, and I remembered that the bootloader would be on the XP hard drive (is this correct?)

How should I reinstall GRUB so that I can dual boot xp and Ubuntu again?

---

### Post by tsger on 2009-01-07
Try these intstructions: [http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by civillian on 2009-01-07
that worked great, thanks :D

what do i have to do to get xp to show up in the boot menu?

---

### Post by tsger on 2009-01-07
What do you see when you run ```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by vikasmk on 2009-01-07
XP should show up in the boot menu .
 like tsger asked , give us contents of /boot/grub/menu.lst

---

### Post by civillian on 2009-01-07
When I run the command, I get the following

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
# kopt=root=UUID=e6f04bb3-c924-4b60-81a2-e1b40857ff46 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e6f04bb3-c924-4b60-81a2-e1b40857ff46

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

title		Ubuntu 8.10, kernel 2.6.27-10-generic
uuid		e6f04bb3-c924-4b60-81a2-e1b40857ff46
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=e6f04bb3-c924-4b60-81a2-e1b40857ff46 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
uuid		e6f04bb3-c924-4b60-81a2-e1b40857ff46
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=e6f04bb3-c924-4b60-81a2-e1b40857ff46 ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e6f04bb3-c924-4b60-81a2-e1b40857ff46
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e6f04bb3-c924-4b60-81a2-e1b40857ff46 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e6f04bb3-c924-4b60-81a2-e1b40857ff46
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e6f04bb3-c924-4b60-81a2-e1b40857ff46 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e6f04bb3-c924-4b60-81a2-e1b40857ff46
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e6f04bb3-c924-4b60-81a2-e1b40857ff46 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e6f04bb3-c924-4b60-81a2-e1b40857ff46
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e6f04bb3-c924-4b60-81a2-e1b40857ff46 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e6f04bb3-c924-4b60-81a2-e1b40857ff46
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I presume that my xp hard drive/partition (a whole disk partition on sda, making it sda1) would be hd0,0 (for reference later)?

---

### Post by tsger on 2009-01-07
Yes, XP should be on (hd0,0).

Try adding the following to your /boot/grub/menu.lst

```
title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1
```

---

