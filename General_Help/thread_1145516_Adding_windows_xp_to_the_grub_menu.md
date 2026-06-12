---
title: "Adding windows xp to the grub menu"
date: 2009-05-01
forum: General Help
---

### Post by Bennetto on 2009-05-01
I have tried to add windows xp to the grub menu. But when I select it in the grub menu all it says in the top left corner is "starting up".
thanks in advance

menu.lst
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=15a10022-2fe1-4732-ab69-276cafa49c75 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=15a10022-2fe1-4732-ab69-276cafa49c75 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=15a10022-2fe1-4732-ab69-276cafa49c75 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

title      Windows XP Professional
root      (hd1,0)
makeactive
chainloader   +1
### END DEBIAN AUTOMAGIC KERNELS LIST
```

heres a link to a previous post i made when i had linux mint installed. I had the same problem.
[http://forums.linuxmint.com/viewtopic.php?f=46&t=24188&sid=720d945686ea709e16966a930b1d5e80&p=141716#p141716](http://forums.linuxmint.com/viewtopic.php?f=46&t=24188&sid=720d945686ea709e16966a930b1d5e80&p=141716#p141716)

---

### Post by logos34 on 2009-05-01
try adding this:
> 
title Windows XP Professional
root (hd1,0)
[B]map (hd0) (hd1)
map (hd1) (hd0)[/B]
makeactive
chainloader +1

---

### Post by SuperSonic4 on 2009-05-01
Can you post ```
sudo fdisk -l
``` so we can see where XP resides

---

### Post by Bennetto on 2009-05-01
sudo fdisk
```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
240 heads, 63 sectors/track, 38761 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0be00be0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27768   209926048+   7  HPFS/NTFS
/dev/sda2           27769       38761    83107080    7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris
daryl@daryl-ubuntu:~$ 



```

what does the map functions do?

---

### Post by logos34 on 2009-05-01
> **Bennetto said:**
> 
what does the map functions do?

[http://www.gnu.org/software/grub/manual/grub.html#map](http://www.gnu.org/software/grub/manual/grub.html#map)
[http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)


well, does it work?

because if you're getting the "starting up..." message then you've reached the windows ntldr at (hd1,0), so all you need to do is perform a 'virtual swap' to fool xp into thinking it's on the boot disk

---

### Post by Bennetto on 2009-05-02
Thank you very much.
Someone else told me to use the map function a while ago but it rewrote the window mbr.
This time it didn't and it is working great!!!
thank you

---

