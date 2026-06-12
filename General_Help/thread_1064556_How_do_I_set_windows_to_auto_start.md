---
title: "How do I set windows to auto start?"
date: 2009-02-08
forum: General Help
---

### Post by Rickmasta on 2009-02-08
Well, I recently installed Ubuntu onto my computer ( like 2 hours ago, recently). I used the following tutorial to install it to an external hard drive: [http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/) 

My intentions for Ubuntu or Linux period, was to have it as a second OS. Having windows as my main OS. When I start my computer I want it to automatically to start windows, and not Ubuntu, is it possible if anyone can help me?

BTW; I installed ubuntu version 8.10

Thanks in advance!

---

### Post by drs305 on 2009-02-09
If you are using the grub menu during boot, you can easily make windows the default OS.

Install StartUp-Manager:
```

sudo apt-get install startupmanager

```

Run it (or via System, Administration, StartUp-Manager):
```
gksudo startupmanager
```

In the Boot Options, Default Operating System, select Windows.

There are a lot of tweaks StartUp-Manager can make. Read the tutorial, accessed by the link in my signature line.

---

### Post by spcwingo on 2009-02-09
Please post your /boot/grub/menu.lst and we'll see if we can get it sorted.

---

### Post by Rickmasta on 2009-02-09
> **spcwingo said:**
> Please post your /boot/grub/menu.lst and we'll see if we can get it sorted.

Explain how, lol, thanks.
> **drs305 said:**
> If you are using the grub menu during boot, you can easily make windows the default OS.

Install StartUp-Manager:
```

sudo apt-get install startupmanager

```

Run it (or via System, Administration, StartUp-Manager):
```
gksudo startupmanager
```

In the Boot Options, Default Operating System, select Windows.

There are a lot of tweaks StartUp-Manager can make. Read the tutorial, accessed by the link in my signature line.

I did as said, and the only options I have for defult operating systems are, 

[IMG]http://i13.photobucket.com/albums/a287/Rickmasta185/bootoptions.png[/IMG]

---

### Post by spcwingo on 2009-02-09
> **Rickmasta said:**
> Explain how, lol, thanks.

Open gedit (applications>accessiories>text editor), choose open, choose "file system" on the left side of the window, navigate to /boot/grub/menu.lst, and copy/paste in your next post.

---

### Post by Rickmasta on 2009-02-09
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
default		saved

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=596f87fd-eda5-41a1-89c6-1760b1b79652 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=596f87fd-eda5-41a1-89c6-1760b1b79652

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
uuid		596f87fd-eda5-41a1-89c6-1760b1b79652
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=596f87fd-eda5-41a1-89c6-1760b1b79652 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		596f87fd-eda5-41a1-89c6-1760b1b79652
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=596f87fd-eda5-41a1-89c6-1760b1b79652 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		596f87fd-eda5-41a1-89c6-1760b1b79652
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=596f87fd-eda5-41a1-89c6-1760b1b79652 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		596f87fd-eda5-41a1-89c6-1760b1b79652
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=596f87fd-eda5-41a1-89c6-1760b1b79652 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		596f87fd-eda5-41a1-89c6-1760b1b79652
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

There you go! :D

---

### Post by TeoBigusGeekus on 2009-02-09
I'm sorry to be the one to tell you so, but I'm afraid you've lost your windows...
Could you post the output of
```
sudo fdisk -l
```
that's -L.

---

### Post by Rickmasta on 2009-02-09
> **TeoBigusGeekus said:**
> I'm sorry to be the one to tell you so, but I'm afraid you've lost your windows...
Could you post the output of
```
sudo fdisk -l
```
that's -L.

Well, I'm sure i didn't loose my windows. That tutorial said to disconnect your computer's internal drive, to make sure you don't write over it, and that's exactly what I did. I can easily start my vista, and it works perfectly. All I have to do is press F12 when my computer fist starts, and go to the boot menu, then click my internal hard drive, and bam, I'm on vista. I haven't noticed any error with vista since I installed ubuntu.

&, what you requested, 

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1314       60802   477835264    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f995056

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       59572   478512058+  83  Linux
/dev/sdb2           59573       60801     9871942+   5  Extended
/dev/sdb5           59573       60801     9871911   82  Linux swap / Solaris

Disk /dev/sdc: 1986 MB, 1986002944 bytes
62 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

```

---

### Post by spcwingo on 2009-02-09
Almost there...now run and post output of:

```
sudo blkid
```

This will give the UUIDs of your partitions.  Please also add which is your windows partition (I'm assuming /dev/sda3 is it, but want to be sure).

---

### Post by Rickmasta on 2009-02-09
> **spcwingo said:**
> Almost there...now run and post output of:

```
sudo blkid
```

This will give the UUIDs of your partitions.  Please also add which is your windows partition (I'm assuming /dev/sda3 is it, but want to be sure).
Sure, 

```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0610" TYPE="vfat" 
/dev/sda2: UUID="4814A53114A52344" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="0A1CA7A41CA78971" LABEL="OS" TYPE="ntfs" 
/dev/sdb1: UUID="596f87fd-eda5-41a1-89c6-1760b1b79652" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="117843a5-dbfb-4500-aebf-a6d079f488ce" 
/dev/sdc: LABEL="Insignia_SP" UUID="0000-0000" TYPE="vfat"
```

---

### Post by Rickmasta on 2009-02-09
> **spcwingo said:**
> Almost there...now run and post output of:

```
sudo blkid
```

This will give the UUIDs of your partitions.  Please also add which is your windows partition (I'm assuming /dev/sda3 is it, but want to be sure).
Sure, 

```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0610" TYPE="vfat" 
/dev/sda2: UUID="4814A53114A52344" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="0A1CA7A41CA78971" LABEL="OS" TYPE="ntfs" 
/dev/sdb1: UUID="596f87fd-eda5-41a1-89c6-1760b1b79652" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="117843a5-dbfb-4500-aebf-a6d079f488ce" 
/dev/sdc: LABEL="Insignia_SP" UUID="0000-0000" TYPE="vfat"
```

---

### Post by spcwingo on 2009-02-09
Add this to the end of your grub menu.lst:

```
title		Windows
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```

by pressing alt+F2 and typing:

```
gksu gedit
```

Once that is done find the line that looks like this:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		saved
```

and make it look like this:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		5
```

save and reboot.  Gedit will automatically back up you menu.lst, so if for some reason it doesn't work we can always load the old one back up (as long as you still have the live CD).  ;)  Hopefully this will get you up and running...let me know.

---

