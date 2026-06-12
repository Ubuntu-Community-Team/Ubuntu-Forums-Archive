---
title: "need help editing grub"
date: 2009-03-19
forum: General Help
---

### Post by sjpritch25 on 2009-03-19
i installed Vista on another hard drive and need assitence editing grub so I'm able to boot into vista when needed.   thanks.  

I'm not sure if i need to re-install Grub or not.   Thanks again.

---

### Post by taurus on 2009-03-19
If you installed windows after you installed Ubuntu, windows basically wiped out GRUB from MBR so you need to reinstall GRUB to MBR again.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by adzik on 2009-03-19
Does grub still come up after the Vista install or does Vista just boot directly now?

---

### Post by sjpritch25 on 2009-03-20
I tell everyone, it was a pain the you know what to get it installed.  Anyways, i had to unplug the power cord of my ubuntu hard drive to get it installed.   So its on my other hard drive and grub booting into ubuntu fine.

---

### Post by ivanvajar on 2009-03-20
Seems to me you'll be able to boot Vista after changing boot priority in BIOS. :-)

---

### Post by Dr Small on 2009-03-20
Post your GRUB menu:
```
cat /boot/grub/menu.lst
```

Since you have Ubuntu on drive 1, and Vista on drive 2, we should be able to add an option into the GRUB menu to be able to boot drive 2, without swapping BIOS drive boot order around.

---

### Post by ivanvajar on 2009-03-20
If you edit /boot/grub/menu.lst by inserting

> title		Windows
root		(hd1,0)
makeactive
chainloader	+1

does that help?

---

### Post by ivanvajar on 2009-03-20
Yup, let's see what

> cat /boot/grub/menu.lst

says

---

### Post by Yellow Pasque on 2009-03-20
A lot of modern motherboards have an option to select what device you want to boot from each time you start the system. For me, I have a mobo with an AMI BIOS, and I just hit the F9 key if I want to boot from another drive.

---

### Post by ivanvajar on 2009-03-20
We don't want him to switch boot priority, but simply edit GRUB for dual-boot. That is Linux way of doing things :-)

---

### Post by Yellow Pasque on 2009-03-20
> **ivanvajar said:**
> We don't want him to switch boot priority, but simply edit GRUB for dual-boot. That is Linux way of doing things :-)
Read my post again. I wasn't suggesting switching boot priority, but using the option to override the default device if one is available.

---

### Post by adzik on 2009-03-20
If we're understanding the original issue then, you installed Ubuntu on another drive, pulled the power to it to install Vista on a different drive. Is that right?
We need to know specifically what is happening, because the bootloader may have some innacurate information in it at this point...maybe.
Is Vista the primary master hd in you system? Is the ubuntu drive a secondary or is it an external usb drive? What's the situation specifically
Post your grub.lst.

---

### Post by sjpritch25 on 2009-03-20
> **Dr Small said:**
> Post your GRUB menu:
```
cat /boot/grub/menu.lst
```

Since you have Ubuntu on drive 1, and Vista on drive 2, we should be able to add an option into the GRUB menu to be able to boot drive 2, without swapping BIOS drive boot order around.


Here you go
```

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
# kopt=root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, memtest86+ (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

stefan@stefan-desktop:~$ sudo cat /boot/grub/menu.lst
[sudo] password for stefan: 
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
# kopt=root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, memtest86+ (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

---

### Post by sjpritch25 on 2009-03-20
> **ivanvajar said:**
> Seems to me you'll be able to boot Vista after changing boot priority in BIOS. :-)

I have the option but i really would rather fix it in grub anyways.  I'm planning on installing windows 7 my 3rd drive too.

---

### Post by ivanvajar on 2009-03-21
Try adding

> title Windows
root (hd1,0)
makeactive
chainloader +1

at the end of /boot/grub/menu.lst

If that doesn't help post output of

> sudo fdisk -l

---

### Post by sjpritch25 on 2009-03-21
here is fdisk -l

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ecd4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2           60692       60801      883575    5  Extended
/dev/sda3            4864       60691   448438410   83  Linux
/dev/sda5           60693       60801      875542+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93d9f224

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02782bc8

   Device Boot      Start         End      Blocks   Id  System

```


I'm going to reboot and check if i can boot into vista.   Thanks

---

### Post by sjpritch25 on 2009-03-21
It didn't work.

---

### Post by mhgsys on 2009-03-21
You might want to try this Window's entry:


title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)

---

### Post by sjpritch25 on 2009-03-21
still no luck.   If worse comes to worse would re-installing grub work or not?

---

### Post by meierfra. on 2009-03-21
> If worse comes to worse would re-installing grub work or not?

Reinstalling Grub will not help. Your problem  is with menu.lst, not how grub is installed.

Add both of the following entries  to the very end of your menu.lst:

title Windows XP  (hd1)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


title Windows XP  (hd2)
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

Reboot and try both entries. If one of them works, you can delete the other from menu.lst. If none of them work, report all error messages you got.

---

### Post by sjpritch25 on 2009-03-22
> **meierfra. said:**
> Reinstalling Grub will not help. Your problem  is with menu.lst, not how grub is installed.

Add both of the following entries  to the very end of your menu.lst:

title Windows XP  (hd1)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


Nothing happened it just restarted

> title Windows XP  (hd2)
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


i received an error 21 no parition

---

### Post by meierfra. on 2009-03-22
Seems  there is something wrong.

In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.


In addition, at the grub menu at boot up, press "c".
This will get you to the grub command line

Type

```

geometry (hd0)

geometry (hd1)

geometry (hd2)

geometry (hd3)

```

This should show the partitions of your first four  hard drives.
(even if you have less than fours hard drives, try all four commands)

Judging from the output:

Is grub detecting your hard drive correctly?
Which hard drive contains XP?

(Pressing "Esc" will get you back to the grub menu.)

---

### Post by mhgsys on 2009-03-22
please try 

```


title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

 > 
Originally Posted by meierfra.  
Reinstalling Grub will not help. Your problem is with menu.lst, not how grub is installed.

Add both of the following entries to the very end of your menu.lst:

title Windows XP (hd1)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


> 
Nothing happened it just restarted


You both forgot to put in :savedefault
and makeactive

---

### Post by meierfra. on 2009-03-22
> You both forgot to put in :savedefault
and makeactive

I did not forget. They are unnecessary and "savedefault"  is even known to cause problems is same rare cases.

---

### Post by mhgsys on 2009-03-22
> **meierfra. said:**
> I did not forget. They are unnecessary and "savedefault"  is even known to cause problems is same rare cases.

so according to you makeactive isn't necessary to boot?

edit:
Your right, I just tried it on my laptop. (both os's are on 1 disk)

Then why these options?

---

### Post by meierfra. on 2009-03-22
> so according to you makeactive isn't necessary to boot?

"makeactive" puts the boot flag  to the XP partition. But since the boot flag already is  on the XP partition, it does not do anything.
  

If "default saved" is used in menu.lst (instead of say "default 0")   then the "savedefault" in the XP item  makes XP the default boot. So after you booted into XP, XP will be the default boot for the next time you boot the computer.

---

### Post by mhgsys on 2009-03-22
@meierfra

thnx for that information 
makes all sense here.

edit: 

btw did you have a go with :
```

title		Windows NT/2000/XP (loader)
root		(hd0,0)

```

and

```

title Windows XP 
root (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

```

---

### Post by sjpritch25 on 2009-03-22
> 
Is grub detecting your hard drive correctly?
Which hard drive contains XP?

(Pressing "Esc" will get you back to the grub menu.)

okay, i think the problem may be that grub is looking for my second drive because that's where my old XP partition was.   I installed Vista on my 3rd drive, but i had to unplug my linux drive to install it.   After the Vista install, i can boot into ubuntu fine, but not Vista.

---

### Post by sjpritch25 on 2009-03-22
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ecd4f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,124,094    78,124,032  83 Linux
/dev/sda2         975,000,915   976,768,064     1,767,150   5 Extended
/dev/sda5         975,016,980   976,768,064     1,751,085  82 Linux swap / Solaris
/dev/sda3          78,124,095   975,000,914   896,876,820  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x93d9f224

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02782bc8

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0ce59b0b-d402-423c-b880-d75fa60e2f68" TYPE="ext3" 
/dev/sda3: UUID="6ef63394-3ca1-4dae-8082-376374fa7087" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="8b8fb239-c256-4e6c-8ac1-4324426dd966" 
/dev/sdb1: UUID="2C586C66586C30AE" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/stefan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stefan)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Windows XP (hd1)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1



title Windows XP (hd2)
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=211c9cd4-ad57-493e-8373-bbb4ee4226a2 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Ubuntu 7.10, memtest86+ (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ce59b0b-d402-423c-b880-d75fa60e2f68 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=6ef63394-3ca1-4dae-8082-376374fa7087 /home           ext3    relatime        0       2
# /dev/sda5
UUID=8b8fb239-c256-4e6c-8ac1-4324426dd966 none            swap    sw              0       0
# /dev/sdc4
UUID=97878303-8969-4219-bfa6-3cc5e594ccca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  34.9GB: boot/grub/menu.lst
  34.9GB: boot/grub/stage2
  34.9GB: boot/initrd.img-2.6.24-16-generic
  34.9GB: boot/initrd.img-2.6.24-16-generic.bak
  35.0GB: boot/initrd.img-2.6.24-19-generic
  34.9GB: boot/initrd.img-2.6.24-19-generic.bak
  34.9GB: boot/initrd.img-2.6.24-21-generic
  35.0GB: boot/initrd.img-2.6.24-21-generic.bak
  35.0GB: boot/initrd.img-2.6.24-22-generic
  34.9GB: boot/initrd.img-2.6.24-22-generic.bak
  35.0GB: boot/initrd.img-2.6.24-23-generic
  34.9GB: boot/initrd.img-2.6.24-23-generic.bak
  34.9GB: boot/vmlinuz-2.6.24-16-generic
  34.9GB: boot/vmlinuz-2.6.24-19-generic
  34.9GB: boot/vmlinuz-2.6.24-21-generic
  34.9GB: boot/vmlinuz-2.6.24-22-generic
  34.9GB: boot/vmlinuz-2.6.24-23-generic
  35.0GB: initrd.img
  35.0GB: initrd.img.old
  34.9GB: vmlinuz
  34.9GB: vmlinuz.old

---

### Post by sjpritch25 on 2009-03-22
here is the other thing 


hd0 is my linux drive with two ext2 partition and one unknown one which i assume is my swap partition.

hd1 is filesystem type unknown partition type 0X7

hd2 is my second drive with no partition.  I'm planning on installing Windows 7 on this drive.  May not with all of these issues.

---

### Post by meierfra. on 2009-03-22
Neither the  boot info script nor the geometry commands  reveal any problems.

(You did run the geometry command  by pressing "c" at the grub menu and not via "sudo grub", right?)


So I have no clue  what the problems could be.
So instead of trying to figure out that the problem is, lets see whether we can work around it. 

> Seems to me you'll be able to boot Vista after changing boot priority in BIOS

Did you ever try this?  If this works we will at least know that there is nothing wrong with Vista.  And you could add Ubuntu to the Vista boot loader.

---

