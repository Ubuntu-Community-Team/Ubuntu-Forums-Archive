---
title: "Grub error 17"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Enigmatic on 2006-08-24
Not quite sure what I did, but I had to reinstall Ubuntu. I formatted the / partition, and then made a new swap as well. 

However when booting I always get grub error 17. 

I tried the steps here:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=mount+drives+livecd](http://ubuntuforums.org/showthread.php?t=224351&highlight=mount+drives+livecd)

And it will find and install grub without a problem, but it never actually changes anything.

Ideas?

---

### Post by LKRaider on 2006-08-24
Please report how your disks/partitions are setup.

This error seem to occur because of old/buggy BIOS and/or because the /boot partition is not on the first disk or within the first 1024 cylinder (~8.5GB area).

Also, if you are using SATA drives with a controller card, you may need to place the /boot partition on an ide drive.

Since this is usually because BIOS problems, upgrading the BIOS could solve this too.

---

### Post by Enigmatic on 2006-08-24
When I first started with Ubuntu I had sda (250GB) and sdb (200GB).

I added a 320GB, which became sda and bumped the others down by one. It was a big pain because I had to manually edit my grub conf everytime I updated my kernel as it was pointing to the wrong drive.

Not sure if that would have anything to do with it. I looked at the menu.lst and it seems fine to me.

Don't think it would be BIOS, as I haven't touched it since I started with Ubuntu 2 months ago. SATA drives are on the mobo and not on a controller card, so it should be okay without a boot partition on an IDE drive.

---

### Post by LKRaider on 2006-08-25
The error means grub cannot identify the filesystem:

> "Error 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

You should check if the Grub root option is pointing to the right device in menu.lst . Find a line similar to this:
```
# groot=(hd0,1)
```
the (hd0,1) should actually point to your /boot partition.



Also, a few lines up this option, you will find a line similar to this:
```
# kopt=root=/dev/hda5 ro
```
Edit this line to point to your linux partition, the one you said you had to change everytime you installed a new kernel. This line actually causes the change when you update the kernel.

---

### Post by Enigmatic on 2006-08-25
Actually, they are both pointing to hd1,3 and sdb4, so I'm not sure what the problem is as the options are correct.

---

### Post by anaconda on 2006-08-25
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

I don't know about the kopt-line, but this # groot .. line defines in which disk and partition is your linux... And each time kernel is changed it reads from the # groot -line..  I had this same problem, until  I changed this line.

And as you propably know (hd0,2) means first hard-disk and partition number 3..eg. the numbering starts from 0 (not 1)

And the hd where your grub:s first stage is loaded from. IS your  first hd. (hd0,x)

I think your problem is that neither you nor you grub know the real order of your hard-disks. Try all variations, you dont have so many possibilities (just 3since the partition number is propably correct)

try hd0,3 hd1,3 hd2,3
(and sda4  sdb4  sdc4 respectively) 
in the grub menu select 'e' and edit the lines.. if one doesn't work just reboot and try another..

---

### Post by Enigmatic on 2006-08-25
Well, the groot seems to be correct at (1,3) as that is where my partition for Linux is. Here is the whole menu.lst:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default0
 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout10
 
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
# titleWindows 95/98/NT/2000
# root(hd0,0)
# makeactive
# chainloader+1
#
# titleLinux
# root(hd0,1)
# kernel/vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sdb4 ro
 
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,3)
 
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
 
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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
 
## ## End Default Options ##
 
titleUbuntu, kernel 2.6.15-23-386
root(hd1,3)
kernel/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb4 ro quiet splash
initrd/boot/initrd.img-2.6.15-23-386
savedefault
boot
 
titleUbuntu, kernel 2.6.15-23-386 (recovery mode)
root(hd1,3)
kernel/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb4 ro single
initrd/boot/initrd.img-2.6.15-23-386
boot
 
titleUbuntu, memtest86+
root(hd1,3)
kernel/boot/memtest86+.bin 
boot
 
### END DEBIAN AUTOMAGIC KERNELS LIST
 
# This is a divider, added to separate the menu items below from the Debian
# ones.
titleOther operating systems:
root
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
titleMicrosoft Windows XP Professional
root(hd1,1)
savedefault
makeactive
map(hd0) (hd1)
map(hd1) (hd0)
chainloader+1
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb5
titleMicrosoft Windows XP Home Edition
root(hd1,4)
savedefault
makeactive
map(hd0) (hd1)
map(hd1) (hd0)
chainloader+1

---

### Post by Enigmatic on 2006-08-25
I was able to get it fixed. I plugged the drive I installed Ubuntu on into the SATA1 slot, and also made sure to make that the preferred boot drive. Then reinstalled Ubuntu (instead of rebuilding grub) and all is well.

---

### Post by LKRaider on 2006-08-25
Could you please post the exact error that appears? It should list the kind of filesystem it is detecting. Like this:
> filesystem type unknown partition type 0xc
Error 17 : Cannot mount selected partition
The "type 0xc" is important (a FAT32 in this case).

Also, do the other boot options start correctly?


Meanwhile, here are a few things to try:

Is the harddisk setup in your BIOS set as Autodetect? If so, try configuring it correctly manually.

Try this : [http://www.ubuntuforums.org/showpost.php?p=1344969&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1344969&postcount=8)

Get to the grub prompt and type: ```
find /vmlinuz
``` And report what grub tells you.

---

### Post by LKRaider on 2006-08-25
Oh, you got it. Great :)

So, Grub has issues booting from the second SATA it seems.

Maybe it sees the drives in a different order or somesuch?
I just found this: [http://www.linuxquestions.org/questions/showthread.php?p=2283784](http://www.linuxquestions.org/questions/showthread.php?p=2283784)

---

