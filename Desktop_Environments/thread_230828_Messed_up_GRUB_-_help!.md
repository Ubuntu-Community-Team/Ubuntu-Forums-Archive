---
title: "Messed up GRUB - help!"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Morbett on 2006-08-06
I was trying to alter my /boot/grub/menu.lst in order to have suspend2 work.

(I followed the guide here, except I unfortunately erased the "ro" at the end of the "kopt= ..." line).

After I erased that "ro", I couldn't boot Ubuntu any more.  On my upsplash screen, it gets stuck at "Waiting for root file system..."

I've been trying to figure out how to fix my system.  I have an Ubuntu live CD and have been tring a few things in GRUB within the live CD, but so far no luck.

My main Ubuntu partition is hda1.  My other (small) partitions are hda2 and hda5.  FYI, when I altered the /boot/grub/menu.ls, I included hda5.  So I replaced the "kopt=" line with "kopt=resume2=swap:/dev/hda5".  (Originally "ro" came right after this.  So the line was supposed to be "kopt=resume2=swap:/dev/hda5 ro".

I don't want to have to reinstall Ubuntu completely!!  Thank you if you have any suggestions.

---

### Post by fourchannel on 2006-08-06
Ok this could be a simple fix.

GRUB will let you change boot time parameters before launching a kernel.

So when your comp starts up, IF you can see your kernel listed in the GRUB boot menu, press **e**. and it will bring up a listing of all the menu lines related to that kernel. Go to the main kernel line and press **e** again, and this should let you modify the parameters. go and add **ro** to the commands and press enter, followed by **b**. This will then load your kernel with your custom modifications. IF this works don't forget to open up a text editor and make those changes permanent.

If you CAN'T get to grub before your system boots, then you will need a live cd.

I'm going to assume that you have /boot as a folder inside your main partition /dev/hda1

launch the live cd and open up a terminal and run these commands. They make a directory, mount your harddrive and then open a text editor for you to change your menu.lst file.

```
sudo su
mkdir /mnt/hda1
mount /dev/hda1 /mnt/hda1
gedit "/mnt/hda1/boot/grub/menu.lst" ### make your changes and save the new file
exit
``` 
reboot and you should be ok. Post if anything happens or you need some help.

---

### Post by bulldog on 2006-08-06
:d

---

### Post by Morbett on 2006-08-07
Hmmm, thanks for your answer.  I'm still trying to get this figured out.  I had to use your Live CD method.  It allowed me to alter the /boot/grub/menu.lst

I added the "ro", but that didn't do anything upon rebooting.  It still hung during the upsplash screen at "Waiting for root file system", then after a few minutes it goes back to basic text and says things like: "No volume groups found" and "/bin/sh: can't access tty; job control turned off".

So I went and deleted everything from the "# kopt=" line in the /boot/grub/menu.lst.  That still didn't give me any results.  Then I added the following to the "kopt=" line :  "root=/dev/hda1 ro".  That's what I think the default was before I started messing around with it.

I tried rebooting again, but I still can't get past the upsplash.  It still eventually stops and tells me I can't access the tty.

I hope that's not too confusing.  Any more ideas why I can't boot up properly?  Thanks so so much for your help.;)

---

### Post by fourchannel on 2006-08-07
The problem when booting from the live cd, is that it's sometimes hard to distinguish between the liveCD's system files, and your harddrive's system files.

For example if I used a live cd to access my computer, then if I type the command ```
cat /etc/fstab
``` then it will give me the fstab file on the cd. But I don't want that file, so I have to mount my harddrive somewhere inside the livecd and then access the fstab on the harddrive.

to mount something you need 3 basic bits of knowledge: 1.) what is the partition you are going to mount like /dev/hda2 or something, 2.) what is the file type of the partition I'm going to mount, like ext3 (ubuntu uses this by default), and 3.) what folder am I going to attatch this filesystem under - most commonly people will make a folder under the /mnt (stands for mount) directory and then attatch is there.

so the commands I would run to do this would be ```
sudo su
mkdir /mnt/hda1
mount -t ext3 /dev/hda1 /mnt/hda1
######then If i want to access the grub boot loader file on the harddrive I would then type
gedit /mnt/hda1/boot/grub/menu.lst
#and when you restart the changes you made in that file should have an effect.
exit
``` 
If all else fails, then copy and paste the contents of these files so we can see what's going wrong.
```
/mnt/hda1/boot/grub/menu.lst
/mnt/hda1/etc/fstab
/etc/fstab ### the file the the Live cd uses, not the one off the harddrive.
``` 
I hope that helps. Post back with what you find.

---

### Post by Morbett on 2006-08-07
If all else fails, then copy and paste the contents of these files so we can see what's going wrong.
```
/mnt/hda1/boot/grub/menu.lst
/mnt/hda1/etc/fstab
/etc/fstab ### the file the the Live cd uses, not the one off the harddrive.
``` 
I hope that helps. Post back with what you find.[/QUOTE]

I am able to access the file and alter the kopt= line, but it seems that the changes I make don't affect anything.  I'm also not entirely sure what line was there before I started messing around with it.  As you can see, I put the example given in the file.

So I'll post you the contents of those 3 files.

/mnt/hda1/boot/grub/menu.lst:

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
default		0

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
# kopt=

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

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-686 resume2=swap:/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-686 resume2=swap:/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 resume2=swap:/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 resume2=swap:/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 resume2=swap:/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 resume2=swap:/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST



/mnt/hda1/etc/fstab  :

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0




/etc/fstab  :

> unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0


Maybe you will be able to see what need tinkering.  Thank you again.

---

### Post by Dubbayoo on 2006-08-07
boot one of the alternative grub entries...surely you didn't change them all?

---

### Post by fourchannel on 2006-08-07
Ok I re-wrote a few parts of your grub file, basically I dropped the usage of #kopts= and instead went for the old fashioned way. If this works then I would say feel free to switch over to the #kopts functionality (personally I have never minded having the same info listed a lot, normally I keep my kernels to a minimum).

/boot/grub/menu.lst ```
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(, grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.

default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).

timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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

##kopt_2_6_15=root=/dev/hda1 ro



## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
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
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
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
## ## End Default Options ##

title        Ubuntu, kernel 2.6.15-26-686
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-686 resume2=swap:/dev/hda5 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-686
#savedefault
boot

title        Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-686 resume2=swap:/dev/hda5 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-26-686
boot

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-386 resume2=swap:/dev/hda5 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
#savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-386 resume2=swap:/dev/hda5 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 resume2=swap:/dev/hda5 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386
#savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 resume2=swap:/dev/hda5 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
``` Let me know how this goes.

---

### Post by Morbett on 2006-08-08
Fourchannel, your suggestion worked.  My computer is running normally again.  I truly appreciate the time you took to help me!

I'll look into your wiki on folding@home.  It sounds interesting.

Thanks again.

---

### Post by fourchannel on 2006-08-08
> **Morbett said:**
> Fourchannel, your suggestion worked.  My computer is running normally again.  I truly appreciate the time you took to help me!

I'll look into your wiki on folding@home.  It sounds interesting.

Thanks again.

Glad I could help, but credit for the wiki goes to the folding community not just me.

---

