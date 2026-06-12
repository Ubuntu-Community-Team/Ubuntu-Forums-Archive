---
title: "Error 15 and GRUB Problems..."
date: 2009-06-03
forum: General Help
---

### Post by TetonsGulf on 2009-06-03
I'm getting nowhere with correcting an Error 15, which I know (believe) means that the information required to boot is not where it belongs or where Grub thinks that it is... I'm just not getting anywhere with trying to fix it... the changes are not working and I'm getting file not found errors trying to boot into Ubuntu.

I've tried the fixes at [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113) and I've tried editing from a grub shell. It's not my first trip to the boards for help, but it's the first time something has baffled me when it should be real simple.

I'm running a box with two HD's, one Ubuntu Jaunty and one Vista. These are long standing installs, nothing really "new" to them. The only thing I can think of is I did a Restore to Default option with Usplash this afternoon, but I'm not sure how that plays in.

In the hours spent trying to "repair" this situation, I've now edited myself into having to "e" at the Grub screen and "e" to even bring up Vista... It's a mess!

I'm looking for some patience and some knowledge here, I'd love to know WHAT I did, as I am getting some assistance from the Ub community on how to get my computer back.

Any suggestions?

---

### Post by QIII on 2009-06-03
This may be worth a look.

I had a similar problem with a dual boot a few years ago, so I couldn't tell you for sure what I did.

But this seems vaguely familiar, and more recent.

[http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/)


Also, have you recently changed the size of your swap or anything like that?

---

### Post by qixil on 2009-06-03
I cheated and created a new Ubuntu install... although I now appear to have two grubs... the operational one only being editable through the new install...

---

### Post by TetonsGulf on 2009-06-04
QIII - I tried that route as well... still no luck...

I have made no changes to the Swap or any of the partitions, that I am aware of.

qixil - I suppose that is an alternative, but I'm wanting to NOT reinstall completely. I guess if it comes to it, I could install side by side, copy the important files and then dump the old system, but I think I'd prefer getting the system to work!

Just to have a fresh set of eyes, fdisk -l shows:

/dev/sda1 is boot Linux
/dev/sda2 Extended
/dev/sda5 Linux Swap/Solaris

/dev/sdb1 is boot HPFS/NTFS

and when I'm editing from a grub prompt I'm using (hd0,0). That is correct, right?

Also, once I've done the grub changes, my attempt to boot gives me this message:

From Ubuntu 8.10, kernel 2.6.27-11-generic
Boot from (hd0,0) ext3  22a15ae1-630b-46d3-bd58-84e4d0e9697b
Error 15: File not found

From Ubuntu 8.10, kernel 2.6.27-7-generic
Boot from (hd0,0) ext3  22a15ae1-630b-46d3-bd58-84e4d0e9697b
Error 15: File not found

Recovery Modes do the same things

Thanks for the help, thus far folks, keep it coming!

---

### Post by QIII on 2009-06-04
Could you post your menu.lst in full?

I'm a software developer.  There are plenty of times when something is not working and I debug through the code for hours and never find what is wrong.  When I ask someone to look over my shoulder, invariably he says "Ah, well there it is!"  An hour later, he's telling me he can't figure out what is going wrong and I look over his shoulder for ten seconds and say "Ah, well there it is!"

Being humans, we often see what we think we should see, rather than what is there.  Which is why code is always peer evaluated and then sent to testers for them to wreck our fine plans by saying something isn't working.

A second set of eyes could help.  Maybe.

That'll be our first step.  It could be that you are trying to boot from the wrong devices and you are seeing what you want to see and missing it.

From there, we can go to the next step -- the reason why I was asking if you had changed your swap partition.

I got this from someone else having similar problems.  Your mileage may vary.  CAREFUL!  Any time anyone, including me, suggests a series of commands in the terminal, it is worthwhile to get a second opinion.  Hopefully someone will drive by and be able to confirm or deny this. I ran through steps 1 - 3 (without making edits) on my "test" machine (I keep a fresh install on another machine so I can putter around with suggested commands in the terminal and just reinstall if I bork something) and didn't toast anything.

1.  sudo blkid to get the uuids of your partitions.  (Dont worry about the Vista one right now if it is on a different HDD and you can boot into it.)
2.  sudo gedit /etc/fstab to make sure the uuids are correct there.
3.  sudo gedit /etc/initramfs-tools/conf.d/resume to check the uuid for the swap there is the same as you got from blkid.
4.  sudo update-initramfs -u   
5.  restart

---

### Post by TetonsGulf on 2009-06-04
Here's the menu.lst

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
# kopt=root=UUID=22a15ae1-630b-46d3-bd58-84e4d0e9697b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=22a15ae1-630b-46d3-bd58-84e4d0e9697b

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
# howmany=1

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		22a15ae1-630b-46d3-bd58-84e4d0e9697b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=22a15ae1-630b-46d3-bd58-84e4d0e9697b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		22a15ae1-630b-46d3-bd58-84e4d0e9697b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=22a15ae1-630b-46d3-bd58-84e4d0e9697b ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		22a15ae1-630b-46d3-bd58-84e4d0e9697b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=22a15ae1-630b-46d3-bd58-84e4d0e9697b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		22a15ae1-630b-46d3-bd58-84e4d0e9697b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=22a15ae1-630b-46d3-bd58-84e4d0e9697b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		22a15ae1-630b-46d3-bd58-84e4d0e9697b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by TetonsGulf on 2009-06-04
Here's a check of the UUIDS

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="22a15ae1-630b-46d3-bd58-84e4d0e9697b" TYPE="ext3" 
/dev/sda5: UUID="0e754f28-2132-4506-8b25-eb974af0ec8f" TYPE="swap" 
/dev/sdb1: UUID="26329E84329E591F" TYPE="ntfs" 




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=22a15ae1-630b-46d3-bd58-84e4d0e9697b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=0e754f28-2132-4506-8b25-eb974af0ec8f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0




RESUME=UUID=0e754f28-2132-4506-8b25-eb974af0ec8f
```

---

### Post by QIII on 2009-06-04
All the linux uuids seem to match.

Did you say you are able to boot into Vista?

One thing that I see that is strange is this:

blkid gives your device for your linux uuids as sda1 and ntfs as sdb1

That seems to indicate to me that the second drive (hd1) is your NTFS drive.

But fstab seems to be associating sdb1 with your linux uuids.

And in your menu.list, you have:


title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I think my menu.lst has hd1 in the root line for Vista. (But then, that drive is on the second SATA header and my Ubuntu drive is on the first.)  Anyway, what you have looks like what was automagically put in your menu.lst, so I wouldn't be in a hurry to change it.  And determination of hd0/hd1 is generally dependent on which actual SATA header the drives are connected to.

I'll take a closer look at my machines when I get home tonight and see if I can make any suggestions from that.

---

### Post by zeex on 2009-06-04
Hi, 

Run this script [http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/") 

```
$ sudo ~/Desktop/boot_info_script*.sh
```

It'll generate a file RESULTS.txt with complete boot information of your system. Please post this file here. It might provide more information about your system to solve your boot issue.

:)

---

### Post by TetonsGulf on 2009-06-04
All-

The suggestions worked, I made a trip over to [http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/) and asked for some specific help there as well, and I'm up and running with no issues to Ub or Vista boots!

Thanks many times over for this community, it works wonders!

KSH

---

### Post by zeex on 2009-06-04
> **TetonsGulf said:**
> All-

The suggestions worked, I made a trip over to [http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/) and asked for some specific help there as well, and I'm up and running with no issues to Ub or Vista boots!

Thanks many times over for this community, it works wonders!

KSH

Hi, 

Please post your solution here. How did you make it work ?

---

