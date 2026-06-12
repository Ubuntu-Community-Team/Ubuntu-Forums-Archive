---
title: "can't boot into windows from grub"
date: 2008-12-31
forum: General Help
---

### Post by zachbb on 2008-12-31
The other day I used GParted to move my windows partition to the end of my hard disk, and make my linux partition bigger. Now windows will no longer boot.

What happens is:
I see the GRUB boot loader
Select Windows
Screen says "starting up..."
Screen goes black
Computer Restarts



I saw in some similar posts that people were asking for a copy & paste of "/boot/grub/menu.lst" and "sudo fdisk -l", so here they are:

fdisk:
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2851    22900626    5  Extended
/dev/sda2   *        2852        3511     5301450    7  HPFS/NTFS
/dev/sda3            3512        9729    49946085    7  HPFS/NTFS
/dev/sda5               1        2559    20555104+  83  Linux
/dev/sda6            2560        2851     2345458+  82  Linux swap / Solaris



menu.lst:
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default saved

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
# kopt=root=UUID=29f2c844-3e32-47d1-a28f-4dadb95d11f5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=29f2c844-3e32-47d1-a28f-4dadb95d11f5

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
uuid		29f2c844-3e32-47d1-a28f-4dadb95d11f5
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=29f2c844-3e32-47d1-a28f-4dadb95d11f5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		29f2c844-3e32-47d1-a28f-4dadb95d11f5
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=29f2c844-3e32-47d1-a28f-4dadb95d11f5 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		29f2c844-3e32-47d1-a28f-4dadb95d11f5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=29f2c844-3e32-47d1-a28f-4dadb95d11f5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		29f2c844-3e32-47d1-a28f-4dadb95d11f5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=29f2c844-3e32-47d1-a28f-4dadb95d11f5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		29f2c844-3e32-47d1-a28f-4dadb95d11f5
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
makeactive
chainloader	+1
 

Any ideas?

---

### Post by zachbb on 2008-12-31
Edit: I just included fdisk in my original post.

---

### Post by fooman on 2008-12-31
open /boot/grub/menu.lst for editing with this command:

```
 gksudo gedit /boot/grub/menu.lst
```

scroll down to the windows entry and change the " root        (hd0,2)" to " root        (hd0,1)".  so that it looks like this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
makeactive
chainloader    +1                      
```save and close the file,  then try to boot into windows.

hope that helps.

---

### Post by louieb on 2008-12-31
If windows is in sda2 change the root line from **root (hd0,2)** to [B]root (hd0,1)  in /boot/grub menu.lst.

[/B]If windows  is in sda3 use Gparted to remove the boot flag from sda2 and add the boot flag to sda3.

Good Luck.

---

### Post by zachbb on 2008-12-31
Thank you both for your replies.

Gparted says my windows partition is on sda3.


> **louieb said:**
> change the root line from **root (hd0,2)** to [B]root (hd0,1)  in /boot/grub menu.lst.

When I do that I get this on the screen:
"BOOTMGR Missing...
 Press Crtl+Alt+Del to restart..."



> **louieb said:**
> 
remove the boot flag from sda2 and add the boot flag to sda3.

When I do this, the screen goes black and it restarts, the same symptoms as what I had originally..

---

### Post by louieb on 2008-12-31
A couple of regulars on the forum created a script to diagnose boot problems.  Please run it and post the results.txt file back here.

Heres how to run [http://ubuntuforums.org/showpost.php?p=6458942&postcount=2](http://ubuntuforums.org/showpost.php?p=6458942&postcount=2)

BTW you don't need the live CD to run it You can run it from your Ubuntu hdd install.

---

### Post by caljohnsmith on 2008-12-31
Zachbb, unfortunately no amount of Grub trickery is going to help you boot Windows if you moved Windows from its original location on the drive; the sector starting position of the Windows partition is hard-coded into the Windows boot sector, and Windows breaks if you move the start of its partition. It is possible with quite a bit of effort to fix Windows, but it is not trivial to do so. Can you mount the partition, save your important data, and then reinstall Windows? If that is not a viable option, I know someone who has successfully gotten Windows to boot after moving the starting point of its partition, but you would have to wait for his help. Let me know what you want to do.

---

### Post by zachbb on 2008-12-31
> **caljohnsmith said:**
> Zachbb, unfortunately no amount of Grub trickery is going to help you boot Windows if you moved Windows from its original location on the drive; the sector starting position of the Windows partition is hard-coded into the Windows boot sector, and Windows breaks if you move the start of its partition. It is possible with quite a bit of effort to fix Windows, but it is not trivial to do so. Can you mount the partition, save your important data, and then reinstall Windows? If that is not a viable option, I know someone who has successfully gotten Windows to boot after moving the starting point of its partition, but you would have to wait for his help. Let me know what you want to do.

Thanks for your reply, it's very informative. I will save my data and reinstall.

Just out of interest, does Ubuntu also hardcode the starting position into the boot sector? 

Thanks 

Zach

---

### Post by caljohnsmith on 2008-12-31
> **zachbb said:**
> 
Just out of interest, does Ubuntu also hardcode the starting position into the boot sector? 

Thanks 

Zach
Fortunately not, Ubuntu/Linux does not hard-code the partition starting position into the boot sector unlike Windows; Linux is a lot more robust when it comes to moving/resizing partitions, so you can resize/move Linux partitions without much effort. The only thing to be aware of when you resize a linux partition is that its UUID will typically change, so you have to deal with that sometimes. If you run into any problems after reinstalling Windows, let us know, but otherwise good luck and hope you don't run into any major problems. :)

---

