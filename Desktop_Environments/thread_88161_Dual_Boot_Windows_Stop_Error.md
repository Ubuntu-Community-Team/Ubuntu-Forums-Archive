---
title: "Dual Boot: Windows Stop Error"
date: 2005-11-09
forum: Desktop Environments
---

### Post by Caoimhan on 2005-11-09
Okay, so after I install Ubuntu 5.10 on my system in a dual boot configuration with Windows 2000 Professional, I get a Windows Stop Error in a blue screen when attempting to boot to Windows.

I have a 200 GB Hard Drive with a mainboard that natively supports drives up to 132 GB.  I installed Windows first in a 100 GB partition, and it has been running well on its FAT32 partition for months.  I finally decide to install Ubuntu on the remaining 95 GB of free space.

I did **not** use the special utility disc that came with my hard drive to prep the drive, because I never planned on my DOS/Windows partitions to ever be able to see/use the area of the drive above the 132 GB mark.

Linux has no problem with seeing the additional space, nor with installing itself into that area.  The installation went very smoothly, and Ubuntu is running perfectly.  I can mount my Windows partition in Ubuntu without any difficulty.

GRUB is installed in the MBR, and launches the Windows boot process without a flaw.

However... after I get through the initial black screen with the F8 option at the bottom, and the Windows splash screen comes up, with the blue progress bar... after about 10 seconds, I get a blue screen with (paraphrasing):

```
Windows Stop Error at 0x0000007B (parameter1, parameter2, parameter3, parameter4) UNABLE_TO_ACCESS_DEVICE
```

Any ideas on how I can fix this?

Thanks!
Kevin

---

### Post by GrumpyBob on 2005-11-25
Me too!
Any clues for a resolution?

Edit:  What happened was that I installed Ubuntu 5.10 successfully.  Subsequently I booted into Win2k successfully.  It noticed the partitions had been set up and made some changes.  On the next Win2k boot, it asked if it could instal drivers for new hard drives it had found.  I said no.  Now Win2k will not boot, but gives the "inaccessible_boot_device" error.

I can read files off hda1 (the Win2k ntfspartition), so the disk appears OK. Presumably this is an MBR issue.

I would welcome any advice...

Robert

---

### Post by suRoot on 2005-11-25
You may want to read this:

[http://support.microsoft.com/default.aspx?scid=kb;en-us;305098]("http://support.microsoft.com/default.aspx?scid=kb;en-us;305098")

Perhaps it's applicable in your case.

You may also want to post your Windows boot.ini & grub menu.lst just so we can look at them.

---

### Post by GrumpyBob on 2005-11-25
Just off to check out that link. In the emantime, here are boot.ini and menu.lst

boot.ini:

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect



menu.lst:

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

