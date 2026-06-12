---
title: "Upgraded to Feisty, now grub can't boot"
date: 2007-03-12
forum: Desktop Environments
---

### Post by catfishy on 2007-03-12
Hi!  I've made the mistake of upgrading early to Feisty (although everytime I upgrade I have kernel issues).  I don't even know how to post my grub or config files here because I can't get to a command prompt.  I was getting the message "VFS: cannot open root device.  Please append a correct "root=" boot option ...."  But after researching all last night and today, I haven't been able to give grub something it can use.  My harddrive is like this:
hda (60 gb)
hda1 = windows partition (this one is labeled to "boot" in fdisk)
hda2 = newly upgraded ubuntu feisty

I've tried changing grub where it said:  root=UUID:numberslettersblahblah to ```
root=/dev/hda2
``` but it still refuses to boot it/find it.  My whole reason for upgrading was because Amarok stopped updating my collection and I hoped an upgrade would fix it.  Can you offer any suggestions?

Just figured out how to post these:
device.map
```
(hd0)	/dev/hda
```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5 -- converted during upgrade to edgy
UUID=a9297367-7751-4719-96e2-f381d417ab4e / ext3 defaults,errors=remount-ro 0 1
/dev/hdc        /media/cdrom    udf,iso9660 user,noauto     0       0
#/dev/sda1 	/media/BICYCLE	noauto,rw,owner,umask=000,users	0	0

##/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
##/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
#/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
#/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
#/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
#/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
#/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
```

menu.lst is really long:
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
# kopt=root=UUID=a9297367-7751-4719-96e2-f381d417ab4e ro

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-25-386 root=UUID=a9297367-7751-4719-96e2-f381d417ab4e ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-25-386 root=UUID=a9297367-7751-4719-96e2-f381d417ab4e ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=a9297367-7751-4719-96e2-f381d417ab4e ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=a9297367-7751-4719-96e2-f381d417ab4e ro single
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
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

In the menu.lst, it say (hd0,4) even though there is no partition there apparently....
Also, in my fstab, it says it converted /dev/hda5 to the "UUID=", could that be the problem from when I upgraded eight months ago to edgy?
thank you so much for any help you can offer!  
:)

---

### Post by cyberdork33 on 2007-03-12
sounds like you found the issue...

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)
...
root                (hd0,4)
``` 
is not correct if there are only two partitions...

(hd0,0) = hda1
(hd0,1) = hda2

---

### Post by catfishy on 2007-03-12
That's good to know! but not yet fixed; so I've changed the menu.lst to reflect that the default should be (hd0,1).  I did that by booting into the ubuntu live cd, mounting my ext3 drive and then used gksu nautilus to edit the menu.  But when I restarted the changes weren't in effect (though when I checked next time in the livecd, the changes were still there) (is there a need to* refresh* the files?!.... What could be the issue?  And wouldn't simply editting that grub menu on startup to (hd0,1) at least boot into the /dev/hda2 *that one time?*  But it didn't.  It still gives me the same "please append a correct "root=" boot option".....   Thank you for your help; any further suggestions!  Really, thanks so much, I feel a bit lost....
It keeps telling me as well:

VFS: Cannot open root device "hda2" or unknown-block(0,0)

---

### Post by ebike on 2007-03-12
Did you reftresh your grub by running grub before you re-booted?

IE on the command line type "grub" and follow the prompts ... I remenber having to do this on my laptop some time ago .. I think running it installs some stuff in the MBR. Look up help on grub to understand.

---

### Post by catfishy on 2007-03-13
> **ebike said:**
> Did you reftresh your grub by running grub before you re-booted?


Thank you! Unfortunately I tried that and couldn't get it to boot from the linux partition anywhichway.  With Feisty only a month away, I've decided to start again from scratch.  I was able to backup all my docs using the live disc and an ext. hdd.  I was having kernel issues, so I think it's time to start over.  Thanks for you help; I know I gave up, but dealing with kernel issues is too much for me to handle right now!  I'm zero-ing the drive as I type this.  Thanks!
:KS

---

### Post by yalu on 2007-03-16
Hi,

I solved this problem my way:

boot rescue disk
chroot in installation of ubuntu
```
apt-get install linux-sources-latestblabla (was 2.6.20-something)
```
recompiled the kernel WITHOUT initrd support
installed kernel
modified menu.lst and set the options to the kernel line from 
```
root=UUID=sdfsqfsqfsqfklsfd 
```

to 

```
root=/dev/hda5
```

reboot, and everything nowworks. I get tons of ACPI debug messages though. Maybe that's still turned on because it's a beta release of the kernel package, dunno.

---

### Post by Softpedia on 2007-03-18
Read this to solve the problem:

[http://ubuntuforums.org/showthread.php?p=2317401&highlight=feisty+uuid#post2317401](http://ubuntuforums.org/showthread.php?p=2317401&highlight=feisty+uuid#post2317401)

---

### Post by catfishy on 2007-03-20
> **Softpedia said:**
> Read this to solve the problem:

[http://ubuntuforums.org/showthread.php?p=2317401&highlight=feisty+uuid#post2317401](http://ubuntuforums.org/showthread.php?p=2317401&highlight=feisty+uuid#post2317401)


That looks great.  Now I wish I had waited before erasing it all... oh well, thanks!

---

### Post by sinaen on 2007-10-26
> **catfishy said:**
> That looks great.  Now I wish I had waited before erasing it all... oh well, thanks!

its pretty simple to correct that. just do a ls -al /dev/disk-by-uuid/
and you have the numbers you need again. :)

---

