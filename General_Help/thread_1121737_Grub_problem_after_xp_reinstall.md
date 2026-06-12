---
title: "Grub problem after xp reinstall"
date: 2009-04-10
forum: General Help
---

### Post by Nidding on 2009-04-10
I'm dualbooting ubuntu and windows xp. But after I have first reinstalled xp home edition and then reinstalled xp pro, I can only choose between ubuntu and the previously installed xp home ed. It seems pretty odd to me, since xp home isn't installed anymore. What can be wrong and can I edit the grub to make it work?

---

### Post by chinmaya_n on 2009-04-10
When u choose the XP home edition in the grub is it pointing to Home edition or XP pro??

---

### Post by Nidding on 2009-04-10
Heh. Guess I left out some pretty relevant info there :)
It seems to be pointing at the home ed. When I choose it, it gives me an "Error 13: Invalid or unsupported executable format".

---

### Post by Elfy on 2009-04-10
Can you run

```
cat /boot/grub/menu.lst
sudo fdisk -l
blkid
```

post results here please

---

### Post by yokohama1970 on 2009-04-10
So you are able to get into grub. That is good. I had the same experience. Until I realized that you are able to edit your gksu gedit /boot/grub/menu.lst. You may change the title of any of your OS choices to your liking, but only the "title." I changed mine to this:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		OTHER OS:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Pro SP3
root		(hd0,0)
savedefault
makeactive
chainloader	+1

you may also change your Ubuntu choices to:

## ## End Default Options ##

title		Ubuntu 8.10(Intrepid)
uuid		d9f6c52a-be78-4263-806c-c594c0929ddf
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d9f6c52a-be78-4263-806c-c594c0929ddf ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10 (Generic)
uuid		d9f6c52a-be78-4263-806c-c594c0929ddf
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d9f6c52a-be78-4263-806c-c594c0929ddf ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10(Recovery Mode)
uuid		d9f6c52a-be78-4263-806c-c594c0929ddf
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d9f6c52a-be78-4263-806c-c594c0929ddf ro single
initrd		/boot/initrd.img 2.6.27-11-generic

make sure to only edit the "title" & save file after finished.

---

### Post by Nidding on 2009-04-10
> **forestpixie said:**
> Can you run

```
cat /boot/grub/menu.lst
sudo fdisk -l
blkid
```

post results here please

Sure...
```
nidding@nidding:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=eb49a5f0-d588-4e91-8451-e8cc15ce8477 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=eb49a5f0-d588-4e91-8451-e8cc15ce8477

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		eb49a5f0-d588-4e91-8451-e8cc15ce8477
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=eb49a5f0-d588-4e91-8451-e8cc15ce8477 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		eb49a5f0-d588-4e91-8451-e8cc15ce8477
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=eb49a5f0-d588-4e91-8451-e8cc15ce8477 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		eb49a5f0-d588-4e91-8451-e8cc15ce8477
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=eb49a5f0-d588-4e91-8451-e8cc15ce8477 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		eb49a5f0-d588-4e91-8451-e8cc15ce8477
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=eb49a5f0-d588-4e91-8451-e8cc15ce8477 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		eb49a5f0-d588-4e91-8451-e8cc15ce8477
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Pro Edition
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```
```
sudo fdisk -l
[sudo] password for nidding: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc9dbdbb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433       16413   112302382+   b  W95 FAT32
/dev/sda3   *       16414       17021     4883760   82  Linux swap / Solaris
/dev/sda4           17022       19457    19567170    c  W95 FAT32 (LBA)

```
and
```
nidding@nidding:~$ blkid
/dev/sda1: UUID="eb49a5f0-d588-4e91-8451-e8cc15ce8477" TYPE="ext3" 
/dev/sda2: LABEL="STORAGE" UUID="307D-67E4" TYPE="vfat" 
/dev/sda3: UUID="19275ab6-3634-4d1f-99d0-433cc5fbf3f9" TYPE="swap" 
/dev/sda4: UUID="E4DD-BFDF" TYPE="vfat" 
/dev/loop0: TYPE="squashfs"
``` 
Hope it's right :)

---

### Post by Nidding on 2009-04-10
> **yokohama1970 said:**
> So you are able to get into grub. That is good. I had the same experience. Until I realized that you are able to edit your gksu gedit /boot/grub/menu.lst. You may change the title of any of your OS choices to your liking, but only the "title." I changed mine to this:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		OTHER OS:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Pro SP3
root		(hd0,0)
savedefault
makeactive
chainloader	+1

you may also change your Ubuntu choices to:

## ## End Default Options ##

title		Ubuntu 8.10(Intrepid)
uuid		d9f6c52a-be78-4263-806c-c594c0929ddf
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d9f6c52a-be78-4263-806c-c594c0929ddf ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10 (Generic)
uuid		d9f6c52a-be78-4263-806c-c594c0929ddf
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d9f6c52a-be78-4263-806c-c594c0929ddf ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10(Recovery Mode)
uuid		d9f6c52a-be78-4263-806c-c594c0929ddf
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d9f6c52a-be78-4263-806c-c594c0929ddf ro single
initrd		/boot/initrd.img 2.6.27-11-generic

make sure to only edit the "title" & save file after finished.

Okay but I'm still learning, so how do I figure out exactly what to put in the XP Pro boot option?

---

### Post by Nidding on 2009-04-10
I think I figured it out. I edited the /boot/grub/menu.lst to
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
# kopt=root=UUID=eb49a5f0-d588-4e91-8451-e8cc15ce8477 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=eb49a5f0-d588-4e91-8451-e8cc15ce8477

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		eb49a5f0-d588-4e91-8451-e8cc15ce8477
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=eb49a5f0-d588-4e91-8451-e8cc15ce8477 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		eb49a5f0-d588-4e91-8451-e8cc15ce8477
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=eb49a5f0-d588-4e91-8451-e8cc15ce8477 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

# title		Ubuntu 8.10, kernel 2.6.27-7-generic
# uuid		eb49a5f0-d588-4e91-8451-e8cc15ce8477
# kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=eb49a5f0-d588-4e91-8451-e8cc15ce8477 ro quiet splash 
# initrd		/boot/initrd.img-2.6.27-7-generic
# quiet

# title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
# uuid		eb49a5f0-d588-4e91-8451-e8cc15ce8477
# kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=eb49a5f0-d588-4e91-8451-e8cc15ce8477 ro  single
# initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		eb49a5f0-d588-4e91-8451-e8cc15ce8477
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Pro Edition
root		(hd0,3)
savedefault
makeactive
chainloader	+1

```
It seems to work. Thanks for the help.

---

### Post by yokohama1970 on 2009-04-11
As long as you only changed the "title" to Windows XP Pro or whatever you chose? Basically, when you boot into Windows, you obviously know you have the correct version because it no longer includes "Home Edition" in the "Windows XP" start-up screen. I believe you were concerned because your "Other OS" choices in Grub were not correct "Windows XP Home Edition" not your current upgrade to "Windows XP Professional." That you may edit (update) manually in the "title" portion of "sudo gksu gedit/boot/menu.lst"
Sadly, there arises a need for Windows (not Vista) such as work or PC Gaming. Thank goodness for Ubuntu 8.10, it is much easier & works so well.

---

### Post by callie510 on 2009-04-11
Hahah, I thought i had a similar problem after I wiped Windows Vista and "upgraded" my windows partition to Windows XP. Then I booted from the Live CD and fixed grub the usual way (find, root, setup)

Oddly, my GRUB still says Windows Vista/Longhorn Boot Loader. I wondered if the installation had gone right for a while. Maybe I should go into my menu.lst and change that...

---

### Post by vanweezy on 2009-04-11
I am dual booting windows xp 64 pro and ubuntu.  i just upgraded from xp home and now my grub does not have any options for booting into ubuntu.  Help please, i am lost without my linux box!

---

### Post by Elfy on 2009-04-11
> **vanweezy said:**
> I am dual booting windows xp 64 pro and ubuntu.  i just upgraded from xp home and now my grub does not have any options for booting into ubuntu.  Help please, i am lost without my linux box!

You just need to reinstall grub
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Nidding on 2009-04-11
> **yokohama1970 said:**
> As long as you only changed the "title" to Windows XP Pro or whatever you chose? Basically, when you boot into Windows, you obviously know you have the correct version because it no longer includes "Home Edition" in the "Windows XP" start-up screen. I believe you were concerned because your "Other OS" choices in Grub were not correct "Windows XP Home Edition" not your current upgrade to "Windows XP Professional." That you may edit (update) manually in the "title" portion of "sudo gksu gedit/boot/menu.lst"
Sadly, there arises a need for Windows (not Vista) such as work or PC Gaming. Thank goodness for Ubuntu 8.10, it is much easier & works so well.

The problem was not the name of the boot entry, but that it referred to the old 'home' install which I had replaced with the pro edition. The result was that XP wouldn't boot at all. It works with the changes I made to "sudo gksu gedit/boot/menu.lst", so I'm happy for now.

ps. Yes it sucks to have to use windows, but I need to run a digital audio workstation, for which I yet haven't found any Linux apps that suits my needs :S

---

