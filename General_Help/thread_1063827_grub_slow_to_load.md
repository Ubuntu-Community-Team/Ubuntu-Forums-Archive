---
title: "grub slow to load"
date: 2009-02-08
forum: General Help
---

### Post by aussiedwarf on 2009-02-08
Hi im using a Fujitsu t4010 tablet with intrepid. Recently I have come across the problem that when I start or restart the computer, at the first loading screen (with the fujitsu logo) takes a minute to load when it used to take seconds. 

Next at grub it takes about 30 seconds to get through "GRUB Loading stage1.5.", and another 30 seconds to load "Grub Loading, please wait..."

The next bit loads fine (3 second timer till it loads ubuntu or where i press escape and i get options of what i want to load)

When it starts to load ubuntu it fails and comes up with;
> Gave up waiting for root device. Common problems:
- boot args (cat /proc/cmdline)
-check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/d2ead34b-9489-43a2-8ae9-ce754c99e88c does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)

When i try and exit it comes up with the same message. after about 15 seconds if i exit it loads ubuntu at normal speed and all is 100% (well apart from the fact that the stylus only seems to work 70% of the time where I have to restart and hope that it works).

Now the weird thing  is that If I go into the bios at the beginning and save and exit (no changes made) the computer restarts and loads as normal.

I have tried many things so far. Reinstalling grub did not work. I tried installing damn small linux (I have been wanting to try it out for a while now) which uses grub has the same problem. I tried making a grub partition which did not work.

For reference here is my grubs menu.lst
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
# kopt=root=UUID=d2ead34b-9489-43a2-8ae9-ce754c99e88c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d2ead34b-9489-43a2-8ae9-ce754c99e88c

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d2ead34b-9489-43a2-8ae9-ce754c99e88c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d2ead34b-9489-43a2-8ae9-ce754c99e88c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d2ead34b-9489-43a2-8ae9-ce754c99e88c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d2ead34b-9489-43a2-8ae9-ce754c99e88c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d2ead34b-9489-43a2-8ae9-ce754c99e88c
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

So what can I do to get things working?

---

### Post by aussiedwarf on 2009-02-12
hate to do this but bump.

---

### Post by aussiedwarf on 2009-02-19
hmm, no takers so far.

Well still, I tinkered around a bit. I installed lilo and first all seemed good. 3rd boot later though trouble. lilo boots at normal speed but when it starts to load ubuntu, it ends up at busybox (initramfs) again.  This time though I am getting text updates instead of the graphical boot screen and I get this 3 times

```

ata1: slow to respond ubuntu
ata1:SRST failed (errno=-16)

```

It then goes to busy box. After about a minute Heap of text and I can type exit where ubuntu loads.

---

### Post by Favux on 2009-02-21
Hi aussiedwarf,

Sorry I don't know what's wrong.  If the uuid is recognized, it's recognized.  Why should there be a delay?  In my nearly complete ignorance I would be worrying about my hard drive.  I'd make sure I had a recent backup.  Hope someone helps you soon.

Have you set up your tablet?  I noticed you're using Intrepid.  On another thread dciliske is trying to set up his Fujitsu t4010 tablet in Intrepid.  If you could drop by and help out that would be nice:

[http://ubuntuforums.org/showthread.php?p=6777271#post6777271]("http://ubuntuforums.org/showthread.php?p=6777271#post6777271")

Good luck!

---

### Post by aussiedwarf on 2009-02-22
Thanks for the reply Favux.

Yeah, i'm a little worried that its the actual hard drive as well. Still, I tried a complete wipe of the hard drive. I zeroed all the memory including the partition table. Reinstalled ubuntu and I still had to problem. It just doesn't want to go away. 

Well, now that I just said that I have restarted the computer 5 times in a row without problem. I think I will just have to make sure I keep everything backed up.

---

### Post by rglindley on 2009-04-21
My boot was very slow.  First very slow to start grub, then hanging a minute or so at grub 1.5, then another minute or so at grub loading.  Turned out to be a jumper problem on my boot drive.  I had it jumpered for master with slave present but there was no slave.  Removed the jumper and bang!!  Boots instantly.  But previous Windows XP did not seem to care so I don't really understand what was going on, but now it works great.

---

