---
title: "Vista won't boot after reinstalling grub, help!"
date: 2009-06-18
forum: General Help
---

### Post by MusicMan374 on 2009-06-18
Something must've happened, inside vista, but I can't boot into it anymore. It shows starting up... for a split second and then goes back to the boot menu.

Here is my /boot/grub/menu.lst file:

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=5d91c6cc-d5ad-4dc7-a0b4-feee338f733a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5d91c6cc-d5ad-4dc7-a0b4-feee338f733a

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

title        Windows Vista Home Premium
rootnoverify    (hd0,0)
savedefault
chainloader    +1

# This is a divider.
# (remove pound sign to activate)
#title        Other operating systems:
#root

title        Ubuntu 9.04, (kernel 2.6.28-11-generic)
uuid        5d91c6cc-d5ad-4dc7-a0b4-feee338f733a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5d91c6cc-d5ad-4dc7-a0b4-feee338f733a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, (kernel 2.6.28-11-generic) [recovery mode]
uuid        5d91c6cc-d5ad-4dc7-a0b4-feee338f733a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5d91c6cc-d5ad-4dc7-a0b4-feee338f733a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        memtest86+ (Ubuntu 9.04)
uuid        5d91c6cc-d5ad-4dc7-a0b4-feee338f733a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```I don't see anything in particular wrong with the vista entry, it hasnt changed but all of the sudden I can't boot into it.

Also, when I try to mount the ntfs partition it says Can't mount file. This probably has something to do with vista not booting, and somehow I get the sense it isn't a grub issue..

here is the result of fdisk -l:

```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c66768c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       85104   683597848+   7  HPFS/NTFS
/dev/sda2           85105       91201    48974152+   5  Extended
/dev/sda5           85105       90575    43945776   83  Linux
/dev/sda6           90576       91201     5028313+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4081b04b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244197012    7  HPFS/NTFS

Disk /dev/sdg: 8054 MB, 8054636032 bytes
8 heads, 32 sectors/track, 61451 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       61452     7865839+   7  HPFS/NTFS
```
sda is my internal 750GB hard drive, it's partitioned like it says. Please help I'm stuck!

---

### Post by merlinus on 2009-06-18
Try moving this:

title        Windows Vista Home Premium
rootnoverify    (hd0,0)
savedefault
chainloader    +1

below this:

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by MusicMan374 on 2009-06-18
Tried that. Didn't work. The other thing that it says before it goes back to the menu is Loading grub stage2 at least i think thats what it says.. At least it's something similar. Any other suggestions?

---

### Post by merlinus on 2009-06-18
You might try reinstalling grub from the live cd.  Open a terminal, and assuming ubuntu is on sda5:

```

sudo grub
root (hd0,4)
setup (hd0)
quit

```

---

### Post by MusicMan374 on 2009-06-18
no go.. reinstalled and it didn't change anything. Still reverts back to the menu. The 2 things that make me think that it's a problem with vista is, in ubuntu, when I try to mount, it also is listed as a USB drive for whatever reason and it won't mount. The other is that when I run from my HP provided recovery disks (I removed the recovery partition to free space) It no longer gives me the advanced options for startup repair, system restore, etc., instead it just says factory image recovery, as if it's not detecting vista exists...? WHat could this mean?

---

### Post by merlinus on 2009-06-18
You might try supergrub to boot vista, if you have no original cds.  If that does not work, there may be some serious problems requiring a reinstall.

BTW, is vista on sda1?

---

### Post by MusicMan374 on 2009-06-18
Okay I will try supergrub and post back later. Yea, vista is on sda1, then sda2 contains sda5 and sda6, which are ext3 ubuntu 9.04 and then swap. I used to have recovery partition on sda2 but somehow that partition just stopped working, got corrupted or something after i installed grub over the vista bootloader so i just deleted the partition. Then I reinstalled ubuntu so it was right of vista and then after awhile vista stopped working.

I'll try supergrub thanks for youre help. And btw if vista is not recoverable is there a way to recover files? or do I have to take it to a shop somewhere to have the files recovered?

---

### Post by merlinus on 2009-06-18
You might be able to mount your vista partition under ubuntu.  There are other ways to recover data as well -- testdisk and sysrescue, for example -- and maybe even using knoppix, which is a live linux cd.

---

### Post by MusicMan374 on 2009-06-18
I can't mount it in ubuntu.. I tried that. It says it can't mount the file, plus it says it's a USB drive which is just weird.. not right. Normally before it says 650 GB media or w/e

---

### Post by MusicMan374 on 2009-06-18
Okay well I tried several things in supergrub and none of them worked. Whenever supergrub tried to boot into windows it redirected back to the grub bootloader menu. I think somehow the ntfs boot record on that partition is corrupted or wrongly written. I think it is set to redirect to grub, so when grub tries to boot it windows redirects back to grub. That's my problem so I just need to find a way to rewrite my ntfs boot sector or record or something? Either that or my mbr is corrupted beynd belief but since ubuntu still boots fine I think it's just that partition. Maybe when I installed ubuntu I set an option and it screwed it over? Is there a boot disk that will rewrite the ntfs boot?


EDIT:

I tried mount -t ntfs-3g /dev/sda1 /media/c and i got this result:

```
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

This means my mft is corrupt right? Is there ANY way at all around this?

---

### Post by MusicMan374 on 2009-06-18
Yes i remember an option at the end of the ubuntu installation that I set for grub to be installed on partition 1 and I thought that would just make it easier I don't remember what the hell I was thinking I must've been tired or something. I think I added grub to the NTFS boot record so that screwed up the boot. The mbr i think is fine my partition table is intact at least.

---

### Post by merlinus on 2009-06-18
You may find some of this info helpful:

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#Super_Grub_Disk_Quick_Help](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#Super_Grub_Disk_Quick_Help)

---

