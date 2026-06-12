---
title: "[SOLVED] Ubuntu 8.10 Windows 7 Dual Boot"
date: 2009-01-11
forum: General Help
---

### Post by Patricrawley on 2009-01-11
I can install Windows 7 no problem and I can reboot no problem. But if I fix grub with a live disk or reinstall my system partion to reestablish grub or use GAG as a bootloaded. I can no longer boot W7. The windows loader also fails to recognize Ubuntu. Any suggestions?

---

### Post by logos34 on 2009-01-11
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu)

---

### Post by cariboo on 2009-01-11
I'm going to have to just create a link as this is about the 4th post I've seen with this problem. Relax, and follow [this]("http://ubuntuforums.org/showthread.php?t=224351"), I had the same problem and followed the linked page and was up and running in 5 minutes.

Jim

---

### Post by logos34 on 2009-01-11
> **cariboo907 said:**
> I'm going to have to just create a link as this is about the 4th post I've seen with this problem. Relax, and follow [this]("http://ubuntuforums.org/showthread.php?t=224351")

The OP already has done that:

> **Patricrawley said:**
> But if I fix grub with a live disk

The problem is that grub menu.lst does not know about windows (the latter was installed after linux), so it is necessary to add a windows entry to enable dual-boot

---

### Post by Patricrawley on 2009-01-11
No it sees Windows it just restarts everytime I select it or it just says "Starting Up..." and never goes anywhere.

---

### Post by logos34 on 2009-01-11
> **Patricrawley said:**
> No it sees Windows 

ok, make a liar out of me ;-)

um, post your 

sudo fdisk -l

and 

cat /boot/grub/menu.lst

---

### Post by Patricrawley on 2009-01-11
sudo fdisk -l
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1dd23884

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6324    50795520    7  HPFS/NTFS
/dev/sda2            6325        8756    19535040   83  Linux
/dev/sda3            8757        8999     1951897+  82  Linux swap / Solaris
/dev/sda4            9000       27970   152384557+  83  Linux

```

cat /boot/grub/menu.lst
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
# kopt=root=UUID=51cc5d44-57ad-419c-a84b-7f2d153c6dba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=51cc5d44-57ad-419c-a84b-7f2d153c6dba

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
uuid		51cc5d44-57ad-419c-a84b-7f2d153c6dba
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=51cc5d44-57ad-419c-a84b-7f2d153c6dba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		51cc5d44-57ad-419c-a84b-7f2d153c6dba
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=51cc5d44-57ad-419c-a84b-7f2d153c6dba ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		51cc5d44-57ad-419c-a84b-7f2d153c6dba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=51cc5d44-57ad-419c-a84b-7f2d153c6dba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		51cc5d44-57ad-419c-a84b-7f2d153c6dba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=51cc5d44-57ad-419c-a84b-7f2d153c6dba ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		51cc5d44-57ad-419c-a84b-7f2d153c6dba
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
root		(hd0,0)
makeactive
chainloader	+1

```

---

### Post by logos34 on 2009-01-11
everything looks in order...the fact that you're getting to the windows 'starting up' message means that grub is successfully chainloading it/passing off the boot process, so the problem appears to be on the windows side (but that still doesn't exlain why windows 7 own bootloader can boot it but not when you go via grub).

No experience running windows 7, but you may be able to use [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Linux") to add ubuntu to the windows 7 boot loader.

---

### Post by Patricrawley on 2009-01-11
Using EasyBCD did the trick, thanks. I had to reinstall Windows 7 just to be able to do it though. I did that, then EasyBCD, booted a live disk, set grub up on my ubuntu partition, restarted and bingo! it worked! Thanks again.

---

### Post by Stretsh on 2009-01-11
For future reference, when you get the "Starting up" message before loading Windows, without it going anywhere, try the fix in [this]("http://ubuntuforums.org/showthread.php?t=1037421") post. It worked for me.

---

### Post by logos34 on 2009-01-11
> **Stretsh said:**
> For future reference, when you get the "Starting up" message before loading Windows, without it going anywhere, try the fix in [this]("http://ubuntuforums.org/showthread.php?t=1037421") post. It worked for me.

That's strictly for dual/multi drive, dual boot setups. In this case there's only one hard disk.

---

