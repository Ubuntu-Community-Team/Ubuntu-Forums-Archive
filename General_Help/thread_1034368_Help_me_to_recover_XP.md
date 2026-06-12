---
title: "Help me to recover XP"
date: 2009-01-08
forum: General Help
---

### Post by Julius1988 on 2009-01-08
Recently i reinstalled xp and Ubuntu was gone, so i recoverd Ubuntu using the LiveCD as stated clearly in:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start")
But after recovering Ubuntu i am not able to boot into xp, they tell to modify these lines i dont know how to do it.
> 
 title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
 rootnoverify (hd0,0) #(hd0,0) will be most common, you may need to adjust accordingly
 makeactive
 chainloader +1

outputs of "menu.lst"
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
# kopt=root=UUID=11995748-09f3-4b30-8b59-0184c8210688 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=11995748-09f3-4b30-8b59-0184c8210688

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
uuid		11995748-09f3-4b30-8b59-0184c8210688
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=11995748-09f3-4b30-8b59-0184c8210688 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		11995748-09f3-4b30-8b59-0184c8210688
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=11995748-09f3-4b30-8b59-0184c8210688 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		11995748-09f3-4b30-8b59-0184c8210688
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=11995748-09f3-4b30-8b59-0184c8210688 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		11995748-09f3-4b30-8b59-0184c8210688
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=11995748-09f3-4b30-8b59-0184c8210688 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		11995748-09f3-4b30-8b59-0184c8210688
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


```
"fdisk -l"
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f682f67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0e3b0e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        9561    76790700    f  W95 Ext'd (LBA)
/dev/sdb2   *        9562       19122    76798732+   7  HPFS/NTFS
/dev/sdb3           19123       30087    88076362+  83  Linux
/dev/sdb4           30088       30401     2522205   82  Linux swap / Solaris
/dev/sdb5               2        9561    76790668+   7  HPFS/NTFS


```
There is a copy of xp in 250GB /dev/sdb

---

### Post by albinootje on 2009-01-08
> **Julius1988 said:**
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Try :
```

title		MS-XP on sdb2
root           (hd1,1)
makeactive
map (hd0, hd1)
map (hd1, hd0)
chainloader	+1

```

See also here :
[http://forums.opensuse.org/install-boot-login/385352-vista-xp-respond-grubs-map-function-differently.html](http://forums.opensuse.org/install-boot-login/385352-vista-xp-respond-grubs-map-function-differently.html)

---

### Post by fooman on 2009-01-08
sorry...incorrect

---

### Post by Julius1988 on 2009-01-08
Thanks for ur help guys, problem solved for now:D.But,How did u figure out it was (hd0,1) from the above data?:confused:

---

### Post by Julius1988 on 2009-01-08
Incorrect why?But i am able to boot into xp now,after ur suggestion.

---

### Post by albinootje on 2009-01-08
> **Julius1988 said:**
> Incorrect why?But i am able to boot into xp now,after ur suggestion.

Perhaps you've set the BIOS to boot from dev/sdb instead /dev/sda ?
That would make some sense, because hd(0,1) is the first disk (0), and the second partition on it (1).

---

### Post by Julius1988 on 2009-01-08
Thank You very much

---

