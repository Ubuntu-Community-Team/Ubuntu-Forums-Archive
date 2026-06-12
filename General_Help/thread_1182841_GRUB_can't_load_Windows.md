---
title: "GRUB can't load Windows"
date: 2009-06-09
forum: General Help
---

### Post by Flaphal on 2009-06-09
I recently used gparted to make my vista partition bigger and change some other partitions around, now I find that grub cant boot into vista- trying to do so just takes me straight back to the bios. (booting to ubuntu is still fine though)

I'm guessing this is because the boot sector of the vista partition has moved and grub no longer knows where it is..

How do I go about fixing this? I'm petty sure I've done something very similar in the past but cant remember how I sorted it..

Thanks alot!

(I'm using 8.04)

---

### Post by QIII on 2009-06-09
This guy's problem was not exactly the same as yours, but if you changed partition sizes, you probably changed uuids.  His problem involved booting to Ubuntu, but it might apply.

Take a look at his solution at the bottom of his first post, and see if you can follow it.

Please let us know if this solves your problem.


[http://ubuntuforums.org/showthread.php?t=1167553](http://ubuntuforums.org/showthread.php?t=1167553)

---

### Post by Flaphal on 2009-06-09
I'm afraid I'll need talking through those steps- I'm not sure what those files do and don't really want to be changing stuff without knowing what I'm doing..

---

### Post by Legace on 2009-06-09
> **QIII said:**
> This guy's problem was not exactly the same as yours, but if you changed partition sizes, you probably changed uuids.  His problem involved booting to Ubuntu, but it might apply.

Windows entries don't have UUID's. For example:
```
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

**Flaphal**, post the contents of **/boot/grub/menu.lst** and also post the output of the following command (in Terminal):
```
sudo fdisk -l
```

Please specify which drive contains Windows from the fdisk output.

---

### Post by merlinus on 2009-06-09
FWIW, vista does not like anything but its own disk management tool to be used for resizing, etc. of where it lives.  Many instances of problems using gparted to do this have been reported on the forums.

---

### Post by QIII on 2009-06-09
> **Legace said:**
> Windows entries don't have UUID's.

Actually, they do.  That'll become apparent when he runs sudo fdisk -l.

They don't appear in menu.lst, and I didn't intend to indicate that he should do anything with his windows uuids there. 

But if he posts the results of fdisk -l, we may find that (hd0,0) is not where he's going to need to point his menu.lst.

Correction:  sudo blkid would give him uuids on his Windows partitions.

---

### Post by Flaphal on 2009-06-09
Output of sudo fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          18      144553+  de  Dell Utility
/dev/sda2              19        1324    10485756    7  HPFS/NTFS
/dev/sda3   *        1325        8348    56420280    7  HPFS/NTFS
/dev/sda4            8349       19457    89233042+   5  Extended
/dev/sda5           18935       19457     4200997+  82  Linux swap / Solaris
/dev/sda6            8350       18934    85023981   83  Linux

Partition table entries are not in disk order
```
vista is on sda3

contents of /boot/grub/menu.lst
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
# kopt=root=UUID=64c21ac9-4a76-421b-9709-6d435faa1343 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=64c21ac9-4a76-421b-9709-6d435faa1343 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=64c21ac9-4a76-421b-9709-6d435faa1343 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=64c21ac9-4a76-421b-9709-6d435faa1343 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=64c21ac9-4a76-421b-9709-6d435faa1343 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=64c21ac9-4a76-421b-9709-6d435faa1343 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=64c21ac9-4a76-421b-9709-6d435faa1343 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```


Hope this helps

---

### Post by QIII on 2009-06-09
Take a look at the following, but don't bother with the mkdir stuff.  Your partitions are different.

What you are looking for is the last 4 or 5 posts.

This is from 2008, but since you are using Hardy, the timeframe is about right.

[http://ubuntuforums.org/archive/index.php/t-963714.html](http://ubuntuforums.org/archive/index.php/t-963714.html)

I like TestDisk.

---

### Post by Flaphal on 2009-06-09
I installed and ran testdisk..

It told me the bootsectors weren't matching up, I rebuilt and it told me they matched.

But I'm still getting the same problem: selecting vista just takes me straight back into the BIOS..


Would it be advisable to try using the windows cd to recover? Last time I did this I lost data but that was a long time ago.. maybe its ok now? Also I really expect this will remove GRUB, but I understand that's reasonably easy to replace?

---

### Post by QIII on 2009-06-09
I've always dual booted from separate physical disks after the first time I tried it on a single drive.  I had such a nightmare that I never did it again.

I've seen plenty of posts about doing what you propose, and it seems like people have had good luck.  But it would really be a good idea to back up every scrap of everything you think you might ever want to save before you do anything.

Can you at least mount the Windows partition from Ubuntu?

If you can't TestDisk might be able to help you.  I've recovered a lot of data for people using it from Linux.

Addendum:  Just looked back at your menu.lst.  Take a stab at removing the "savedefault" line.  Boot to Ubuntu, shut down and attempt to boot to Windows.

---

### Post by Flaphal on 2009-06-10
I can mount the windows partition thankfully.. I tried removing the savedefault line but still no change.

I think I'm going to use the windows recovery cd and hope, unless anyone has any better ideas.. I'll post back here letting you know how it all went, and probably will need help getting grub back, unless google is more helpful this time round :)

---

### Post by Entropy_Sam on 2009-06-10
Stop! :-)

You're calling root(0,2), but you can't boot an ntfs partition with root(...)

Change the Vista entry in menu.lst so it reads thus (change is bold/italic/underline):
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root_***noverify***_		(hd0,2)
savedefault
makeactive
chainloader	+1
```

---

### Post by Flaphal on 2009-06-13
I used the vista cd and that sorted it without any trouble.. didnt even mess with grub..

I tried sams trick first but it didnt help

cheers everyone

---

