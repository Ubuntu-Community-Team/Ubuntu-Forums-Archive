---
title: "having trouble dual booting xp"
date: 2009-02-03
forum: General Help
---

### Post by slappy95633 on 2009-02-03
Ok i am a long time windows user trying to make the switch and i am having a hard time.... i need windows for things like my games and a couple other little things that are windows only. and i had a working copy of windows XPSP2 on one partition of the drive some music on another partition and then some free space set aside for ubuntu... i installed ubuntu did all the updates and then went to get onto windows which it shows in grub and it comes up with error 22: no such partition... and i can still access all my windows files on that partition when i am on ubuntu so if anyone has any help on that matter it would be appreciated.

and for some info 

for fdisk:
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27bfc8e3

Device Boot Start End Blocks Id System
/dev/sda1 * 1 24320 195350368+ 7 HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7543b3e

Device Boot Start End Blocks Id System
/dev/sdb1 1 7834 62926573+ 5 Extended
/dev/sdb2 7835 13054 41929650 7 HPFS/NTFS
/dev/sdb3 * 13055 60801 383527777+ 7 HPFS/NTFS
/dev/sdb5 1 373 2996028 82 Linux swap / Solaris
/dev/sdb6 374 7834 59930451 83 Linux

And for the menu list:

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=66650f48-f602-4f87-ad49-97f9071a1526 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=66650f48-f602-4f87-ad49-97f9071a1526

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-11-generic
uuid 66650f48-f602-4f87-ad49-97f9071a1526
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=66650f48-f602-4f87-ad49-97f9071a1526 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid 66650f48-f602-4f87-ad49-97f9071a1526
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=66650f48-f602-4f87-ad49-97f9071a1526 ro single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic
uuid 66650f48-f602-4f87-ad49-97f9071a1526
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=66650f48-f602-4f87-ad49-97f9071a1526 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid 66650f48-f602-4f87-ad49-97f9071a1526
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=66650f48-f602-4f87-ad49-97f9071a1526 ro single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid 66650f48-f602-4f87-ad49-97f9071a1526
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=66650f48-f602-4f87-ad49-97f9071a1526 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid 66650f48-f602-4f87-ad49-97f9071a1526
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=66650f48-f602-4f87-ad49-97f9071a1526 ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
uuid 66650f48-f602-4f87-ad49-97f9071a1526
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title Windows NT/2000/XP (loader)
root (hd0,2)
savedefault
makeactive
chainloader +1

---

### Post by caljohnsmith on 2009-02-03
It sounds like you are booting the Windows sda drive on start up since your current Windows entry in Grub returned an error 22. How about instead trying:
```
title Windows
root (hd0,0)
chainloader +1
```
That's assuming Windows is on sda1, is that true?

---

### Post by slappy95633 on 2009-02-03
yeah it is on the same drive and i will try that right know

---

### Post by slappy95633 on 2009-02-03
it says boot MGR is missing

---

### Post by caljohnsmith on 2009-02-03
Sounds like Vista might be missing its boot files. In order to find out, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Vista booting problem might be.

---

### Post by slappy95633 on 2009-02-03
> **caljohnsmith said:**
> Sounds like Vista might be missing its boot files. In order to find out, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Vista booting problem might be.

umm it is windows xp and when i typed that in it says: 
```
bash: /home/slappy/Desktop/boot_info_script*.sh: No such file or directory
```

---

### Post by slappy95633 on 2009-02-04
bump..... any one else with some ideas

---

