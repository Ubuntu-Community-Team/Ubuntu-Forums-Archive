---
title: "GRUB woes :("
date: 2006-05-31
forum: Desktop Environments
---

### Post by SyntaxTerror on 2006-05-31
Hi guys,

I've just done my second Dapper install in 2 days... Both times I've had some strange issues with GRUB.

First time around the installer correctly found my Win XP installation (same drive as Dapper), and also found another 2 copies of windows 2k on 2 different drives which I also had on the machine (but not booting from, I've been using them to salavge old data off).

GRUB added all these O/S's to the GRUB menu, but here's where things went wrong...

If I chose to boot off WinXP, I'd get the win2k boot loader menu.  If I chose to boot off win2k, I'd get Win XP loading up!

To make matters worse, if I chose to boot Dapper it would say something about not being able to find the o/s!  I could boot it by editing the menu option though and changing hd0,4 to hd0,2 (or something similar).  It's a bit of a shame when the installer can't correctly add it's own operating system it's just finished installing to the boot loader, and doesn't quite make much sense how it could have possibly stuffed it up.

Since then I've gotten rid of the extra drives I had in there, and left the one (split for Win XP and Dapper)

I reinstalled Dapper and it correctly found win XP and added it to GRUB.

Here's the problem:

If I try and boot the PC GRUB simply says 'GRUB Hard Disk Error', and won't let me do anything else.  If I put the Dapper installation cd in and choose 'Boot from first hard drive', it brings up the correct GRUB menu and I can successfully boot Dapper and windows XP without any hassles.

I can't seem to figure out why GRUB stuffs up when booting up.  I've tried doing a grub-install and update-grub from Dapper and it hasn't fixed the issue.  Is there anything else I can try?  In ~7 years of usage I never had a single problem with LILO.  Is it possible to change to LILO without losing the functionality of automatically have the new kernels added to the menu?

Any help on getting GRUB working again would be mostly appreciated.

Cheers,

Ian

---

### Post by matrooswolf on 2006-05-31
Hi, don't really know enough to help you, but try this thread.

[http://ubuntuforums.org/showthread.php?t=119512](http://ubuntuforums.org/showthread.php?t=119512)

see the second post

Working with paritions in Windows once changed their numbers and Grub always reverted to old numbers.  Changing grubs menu.lst as explained in this thread, fixed grub.

Hope it helps.

---

### Post by llamakc on 2006-05-31
You should post your menu.lst for us to see, and the output of `mount` or what's in your /etc/fstab

Did you install grub to the MBR or to hd0,0?

---

### Post by SyntaxTerror on 2006-05-31
Hmm, thanks mate.  Trying to make some sense of it now.

I'll post my menu.lst here just in case.  My immediate reaction was that it wouldn't be menu.lst's fault, since the menus work fine once I boot it by telling the installer cd to boot from the first hard drive.

Anyhow, here's my menu.lst:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/sda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.15-23-686
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin 
boot

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

---

### Post by SyntaxTerror on 2006-05-31
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by SyntaxTerror on 2006-05-31
I think I must have put it in the MBR, but I can't remember to be honest..

If I change:
```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)
```

to groot=(hd0,0)

do you think that would fix it?

---

### Post by hornett on 2006-05-31
When you ran grub-install, what options did you supply?

---

### Post by SyntaxTerror on 2006-05-31
grub-install /dev/sda

---

### Post by SyntaxTerror on 2006-05-31
[QUOTE=hornett]When you ran grub-install, what options did you supply?[/QUOTE]


Should I be giving grub-install any more parameters?  Seems awfully strange that GRUB is failing like this.

---

### Post by SyntaxTerror on 2006-05-31
Also, does my thread really belong in this forum??

---

### Post by mjziegle on 2006-06-01
Sounds like you have problem with your grub install

I suggest booting off the live CD.

Then from the prompt 
>sudo grub
grub>root (hd0,0)
grub>setup(hd0)

This will reinstall grub to the boot sector of your first hard drive.

---

### Post by gatekeep on 2006-06-01
[QUOTE=SyntaxTerror]First time around the installer correctly found my Win XP installation (same drive as Dapper), and also found another 2 copies of windows 2k on 2 different drives which I also had on the machine (but not booting from, I've been using them to salavge old data off).

Since then I've gotten rid of the extra drives I had in there, and left the one (split for Win XP and Dapper)[/QUOTE]

Just to make things clear...the Win XP and Dapper drive is the Primary Master in your machine? And your BIOS is booting FROM that drive? Because, I had a similar problem way back when, and I had GRUB installed on another drive in the MBR (the drive I had the BIOS set to boot from)

---

### Post by SyntaxTerror on 2006-06-01
The way it is for the 'second time around' is that there's only one hard disk in the machine.  It's a SATA drive.  There's no IDE emulation turned on in the BIOS or anything like that.

The drive is considered in linux terms as /dev/sda

Windows is considered as /dev/sda1, and linux is /dev/sda5

I'm considering trying what mjziegle has suggested, that being:
```

>sudo grub
grub>root (hd0,0)
grub>setup(hd0)
```

But I'm worried this might overwrite the windows loader and make that unbootable.  I don't really have enough experience with GRUB to make that call. (I miss you LILO :'( )

Your thoughts?

---

### Post by SyntaxTerror on 2006-06-01
Hey guys, a bit of a bump...

I still don't have this resolved.  A perfect system all set up nicely except I can't boot in to it.

Will running the changes in the post just above this kill my windows partition and make it unbootable?

I'd do it if I had a nicer way to boot windows off the cd.  It's a xp disc with no service packs on it, and I have no disc drive, which means loading the SATA driver aint an easy task.

Any help would be greatly appreciated.

---

