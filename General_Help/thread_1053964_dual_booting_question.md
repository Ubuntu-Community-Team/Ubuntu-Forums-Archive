---
title: "dual booting question"
date: 2009-01-29
forum: General Help
---

### Post by i4w on 2009-01-29
Hey I set up on my pc a dual boot, well basically it is a triple boot. With Windows Vista/Xp and Ubuntu(first time ever using). I installed Ubuntu last so now I use Grub boot loader in the beginning. What I am wanting to do is have it auto select Windows XP(or at least go to Windows boot loader) to boot first after the 10 seconds instead of Ubuntu. I googled it earlier and I know it says to edit the menu.lst under the grub root folder, when I went to it I edited what it said to do and when I clicked save it said I needed permissions etc, so I just backed out of everything. I also was unsure what to change on the guide is says change default to 1, but I didn't know if I needed to change it to 3 because when I go to login my login looks something like this.

[IMG]http://static.screencasts.ubuntu.com/20061204_installing_dual_boot.jpeg[/IMG]

So can anyone give me a step by step guide for a complete noob in ubuntu about how I am supposed to change it? Thanks.

---

### Post by ibutho on 2009-01-29
Hi and welcome to the forums. To edit the file, you need to go to Applications -> Accessories -> Terminal and then do
```
sudo nano /boot/grub/menu.lst
```
You can substitute "nano" for your favourite editor.

---

### Post by -kg- on 2009-01-29
There are two ways you can accomplish this.  With either method you will need to edit your menu.lst file, as shown in the following links:

First method is to change the "default" value:  [Method one]("http://ubuntuforums.org/showthread.php?t=77036")

Second, you can physically change the order of the options:  [Method two]("http://ubuntuforums.org/showthread.php?t=583909")

Read the answers to both of these threads, and they will tell you how to accomplish the task.  In either case, you will need to launch an editor with root permission using the following command in the terminal window...

```
gksu gedit /boot/grub/menu.lst
```

...and then enter your password at the prompt.  Don't worry that you don't see anything happening while you type your password...it won't show astericks or pounds or anything while you type it.  Just go ahead and type in your password.

Menu.lst is a rather long file with a lot of comment lines (i.e., "# comment").  You are looking for lines without the pound sign in front of them.

Should you wish to just change the "default" value (the frist method), the line is near the top of the file.  If you wish to cut and paste the boot lines themselves (the second option), the lines you are looking for are near the bottom.

For a sample, here is my menu.lst file:

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
# kopt=root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

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

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Up near the top you will see:

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
default		0

All the lines down to the last have one or more pound signs in front of them.  For the first example, the last value would be what you're looking to change.  In my case, as I understand it, my "default 0" option is the very first thing in the list towards the bottom of the file:

```
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

```

"Default 1" would be the next set, and so on.  If I were to change the "default" value to autolaunch my Windows first, I would have to change default to "Default 9", since the default setting starts at 0.  The Windows lines are at the very bottom of the file, the others are above it.

If you're looking to change the order of the boot lines themselves, then down at the very bottom you find:

> # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

You would cut and paste these lines above the ones indicated in the thread for the second method:

> #
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

**[COLOR="Red"]PASTE WINDOWS LINES HERE, BEFORE AUTOMAGIC LINE[/COLOR]**

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below


That will physically put Windows before Linux in the boot order, instead of changing the default boot partition by changing the "default" value.

Of course, you can use whatever editor you like or are used to in place of gedit, but to me gedit is the easiest to use.

Good luck!

---

### Post by SteveDee on 2009-01-29
> **i4w said:**
> Hey I set up on my pc a dual boot, well basically it is a triple boot. With Windows Vista/Xp and Ubuntu(first time ever using).....

As you are new to 'buntu I suggest you take the graphical route by using the menus; System > Administration > Startup Manager > Boot options > Default Operating System

You will need to enter your password as an administrative user.

---

### Post by i4w on 2009-01-29
Wow guys thanks for the help! KG you really went all out. I used method #1 because it was the easiest. I changed it to default 4, and it was just that simple. Thanks again!

---

### Post by -kg- on 2009-01-31
> **SteveDee said:**
> As you are new to 'buntu I suggest you take the graphical route by using the menus; System > Administration > Startup Manager > Boot options > Default Operating System

You will need to enter your password as an administrative user.

Quick question, if you read this again:

Is the "Startup Manager" something that has been added to 8.10?  I'm running 8.04 and can't find it under my "System/Administration" menu.

---

### Post by SteveDee on 2009-01-31
> **-kg- said:**
> Quick question, if you read this again:

Is the "Startup Manager" something that has been added to 8.10?  I'm running 8.04 and can't find it under my "System/Administration" menu.

Yes I'm sorry, I can't remember which of my apps were defaults and which I've added myself over the last 12 months.

But if its not in the System > Administration menu then go to Applications > Add/Remove then type "startup" in the "Search:" field. You can then select Startup-Manager and install it.

This application will allow you to control the appearance of your boot menu, what your screen does as the system boots & the default OS.

---

### Post by -kg- on 2009-02-01
Thanks!  I now have it installed, and it's a handy-dandy little piece of software.

---

