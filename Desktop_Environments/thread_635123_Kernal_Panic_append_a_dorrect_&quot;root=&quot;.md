---
title: "Kernal Panic append a dorrect &quot;root=&quot;"
date: 2007-12-08
forum: Desktop Environments
---

### Post by evolving_monkey on 2007-12-08
Hello everyone,
Dual boot Windows XP and Ubuntu 7.04.

So here is what happened. I turned on my computer and no grub loader, just a black screen and three words "no kernal found".  

I then booted with Partition Commander 10 Pro. I chose the Ubuntu install and got these messages.

[    0.947713]  VFS: Cannot open root device "<NULL>" or unknown-block(104,1)
[    0.947713] Please append a correct "root=" boot option
[    0.947765] Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)

Additional info:
-I can successfully  boot to the windows partition from the Partition Commander Pro cd.
-If I use the Ububtu 7.10 live cd (version I had on hand) I can see the contents of the windows partition as well as the Ubuntu partition and have read/write capability. I think I could manipulate files if that becomes part of the solution. 

I am assuming that the grub loader has gotten beat up but this is just a guess. I am still somewhat new to Ubuntu.

Thanks for your help.

---

### Post by taurus on 2007-12-08
Can you post the output of this command when you are in LiveCD?

```
sudo fdisk -l
```
Then, mount your / partition and post your menu.lst, assuming you mount it to /mnt/ubuntu.

```
cat /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by evolving_monkey on 2007-12-08
Thank you Taurus. Here is the info you requested.

Menu.lst

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
# kopt=root=UUID=01b9c53f-3317-425b-b3bf-c0ee0f6ed619 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=01b9c53f-3317-425b-b3bf-c0ee0f6ed619 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=01b9c53f-3317-425b-b3bf-c0ee0f6ed619 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=01b9c53f-3317-425b-b3bf-c0ee0f6ed619 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=01b9c53f-3317-425b-b3bf-c0ee0f6ed619 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

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

Sorry it put faces anywhere there is an 8 at the top. Not sure why.

---

### Post by taurus on 2007-12-08
What if you edit your /boot/grub/menu.lst and change the UUID

```

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.20-16-generic root=**UUID=01b9c53f-3317-425b-b3bf-c0ee0f6ed619** ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```
To 

```

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.20-16-generic **root=/dev/sda5** ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

Save it and reboot.

---

### Post by evolving_monkey on 2007-12-08
That seems to be listed a few times. Should I change all of them?

---

### Post by evolving_monkey on 2007-12-08
I changed the entry that you mentioned (just that one specifically). I rebooted and it said "no kernal". No luck on that one.

---

### Post by evolving_monkey on 2007-12-08
Does anyone have an idea as to what might have caused this to begin with? I have searched the forums and I seem to be the only one that has ever had this error message and posted about it.

---

### Post by evolving_monkey on 2007-12-08
One other thing. A friend of mine said that he agrees that it sounds like grub got blasted. He said that if I run the upgrade via alternative cd to UBUNTU 7.10 it might rebuild the grub and fix the problem. Does anyone have an opinion on that?

---

### Post by evolving_monkey on 2007-12-08
Actually ....I think I remember reading somewhere about reinstalling GRUB. Can anyone either explain how to do that or point me to a good tutorial?

---

### Post by taurus on 2007-12-08
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by evolving_monkey on 2007-12-24
Unfortunately reinstalling grub didn't help. I followed instructions to the letter. I tried a few different forums on this but nobody had a solution. There are folks out there that have had the same problem but no one was able to help them either. I could only find threads with little or no responses. Luckily no valuable data was lost as I don't trust any operating system without a back up.

In the end Linux is occasionally like Windows in that sometimes its just easier to reinstall than fix. So that is what I did. I figure if it's to much for the experts then I probably wouldn't figure it out either.

The upside is that you can get UBUNTU to a usable state typically much faster than Windows. Its all about how well you backup. I have found UBUNTU to be, overall, more stable than Windows. You also seem to get more out of your computer in terms of the amount of ram and processor speed. The problem is that when Linux does blow up it really blows up. That's been my experience anyway.

I still love UBUNTU. I dual boot it with Windows XP but use UBUNTU about %90 of the time. All though that might change a bit now that UBUNTU 7.10 doesn't seem to work with VMWare. (I have to admit that no longer supporting VMWare seems to be pretty counterintuitive but that's another thread.)

---

