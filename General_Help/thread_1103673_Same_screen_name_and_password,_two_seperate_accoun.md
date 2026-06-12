---
title: "Same screen name and password, two seperate accounts.  Please help"
date: 2009-03-22
forum: General Help
---

### Post by Saltwaterfishin on 2009-03-22
Hi all,

I'm totally frustrated with Ubuntu.  Please try to help me with a couple of problems:

1. It seems that I have two (2) accounts under the same screen name on my computer.  When I restart my computer, it asks me my screen name and password as usual.  Using the SAME screen name and password I will be randomly sent to one of two accounts, each with different bookmarks, settings, screen saver, desktop photo and desktop icons.

How can I get this to go to the SAME place each time?

2.  If I don't shut off the power button on the back of the computer, it will turn itself ON when I am not here.  

How can I get it to only turn on when I press the ON button on the front of the computer.

This is just the start of a long list of problems with Ubuntu.  Please help.  You can email me a reply at: [email]Saltwaterfishin@aol.com[/email]

Jay

---

### Post by DGortze380 on 2009-03-22
> **Saltwaterfishin said:**
> Hi all,

I'm totally frustrated with Ubuntu.  Please try to help me with a couple of problems:

1. It seems that I have two (2) accounts under the same screen name on my computer.  When I restart my computer, it asks me my screen name and password as usual.  Using the SAME screen name and password I will be randomly sent to one of two accounts, each with different bookmarks, settings, screen saver, desktop photo and desktop icons.

How can I get this to go to the SAME place each time?

2.  If I don't shut off the power button on the back of the computer, it will turn itself ON when I am not here.  

How can I get it to only turn on when I press the ON button on the front of the computer.

This is just the start of a long list of problems with Ubuntu.  Please help.  You can email me a reply at: [email]Saltwaterfishin@aol.com[/email]

Jay

1) It sounds as if you are having trouble with the X Window System crashing. Can you please provide specs for your computer. I think what is happening is that you log in, when X starts correctly, you get your typical custom desktop. If X fails, you will get default icons, backgrounds, etc. I assure you, you do not have two accounts with the same name and password.

2) You computer is definitely not turning itself on. This sounds like a problem with the BIOS. I've seen a number of old machines that reboot every time instead of shutting down (sometimes with a delay). Again, machine specs would be helpful.

---

### Post by Xiong Chiamiov on 2009-03-23
```

cat /etc/passwd | grep home

```
is an easy way to get a list of non-daemon users on your system (yes, yes, it makes some assumptions about having a home directory, and having it in /home).

You probably don't want your email listed here, although the 3 hours it's been up have probably gotten it on quite a few spam lists already.  We can email you [through the forums](http://ubuntuforums.org/sendmessage.php?do=mailmember&u=784561).

---

### Post by Saltwaterfishin on 2009-03-23
Hi all,

Here is a screen shot for the accounts.  Is this helpful in solving the problem?

---

### Post by Xiong Chiamiov on 2009-03-23
Well, it appears that you only have one user account (jay).  The first three are daemons that, for some reason, need home directories in /home.

Have you installed another desktop environment, such as KDE or XFCE?  More to the point, do the different logins look and act the same, other than desktop etc.?

---

### Post by Saltwaterfishin on 2009-03-24
Hi XIONG,

Thanks for sticking with me.  Each login screen or account is different and they are random.  I don't know how to force the computer to login to the one I WANT to use  For example, the settings that I set on the one I WANT to use only work for that account.  Settings in RHYTHMBOX music player only work for that account.  The background on the one I want to use is a photo of me fishing.  The other account is totally different.  It has the background of UBUNTU.  All settings are different than what I want.  (The computer logged me in to the "bad" account today.

When my brother gave me this computer he mentioned something about dual hard drives.  Could this be causing the problem?  Do you know anything about the "X Window Crashing" as mentioned by another person in this forum?

Thanks again,

Jay

---

### Post by Saltwaterfishin on 2009-03-24
I just shut down and restarted and now I'm on my Prefered account.  I just don't know how to login to this one every time.

---

### Post by lykwydchykyn on 2009-03-24
I suspect this is some kind of problem mounting the home directory, and at random it is failing to mount at boot and giving you a default configuration. 

can you post a comparison of the "mount" command when you have your correct desktop and the incorrect one?  Also, the output of "sudo fdisk -l" would be helpful.

Is your install on two seperate hard drives?

EDIT: also, do you have a phone or mp3 player that you plug in to the computer?  I've experienced this problem on my laptop when my Blackberry was plugged in; for some reason, it wouldn't mount the /home partition and I'd get defaulted.

---

### Post by Saltwaterfishin on 2009-03-25
Thank you for the advice.  Here is a screen shot of the "mount" command for the account I WANT to use.  

As far as the separate hard drives, when my brother gave me the computer he mentioned something about the computer having 2 hard drives

---

### Post by Saltwaterfishin on 2009-03-25
Here is the result of sudo fdisk -l  :

---

### Post by DGortze380 on 2009-03-25
> **Saltwaterfishin said:**
> Here is the result of sudo fdisk -l  :

would you look at that... it appears as though you have two bootable drives. Can you post the output of 

```

cat /boot/grub/menu.lst

```

---

### Post by kpatz on 2009-03-25
You have 2 hard drives in the machine?  Did you clone one to the other?  They both have the same disk identifier, which can/will cause issues.

What's probably happening is when the machine boots, sometimes it detects one as sda and one as sdb, and other times they're reversed.  Your "good" desktop is on one of the 2 drives and the "bad" one is on the other.  You should either remove the 2nd drive or re-partition/put new partitions on it so it gets its own disk ID.

---

### Post by Saltwaterfishin on 2009-03-25
Here is a screen shot of the command "mount" on the account I DON'T want.

I hope this will allow someone to help me solve this problem.

Thanks,

Jay

---

### Post by Saltwaterfishin on 2009-03-25
Here is the result of cat /boot/grub/menu.lst

jay@jay-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=9437d00b-bc2c-451c-9f74-77a99ec9e358 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9437d00b-bc2c-451c-9f74-77a99ec9e358

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
uuid		9437d00b-bc2c-451c-9f74-77a99ec9e358
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9437d00b-bc2c-451c-9f74-77a99ec9e358 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		9437d00b-bc2c-451c-9f74-77a99ec9e358
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9437d00b-bc2c-451c-9f74-77a99ec9e358 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9437d00b-bc2c-451c-9f74-77a99ec9e358
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9437d00b-bc2c-451c-9f74-77a99ec9e358 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9437d00b-bc2c-451c-9f74-77a99ec9e358
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9437d00b-bc2c-451c-9f74-77a99ec9e358 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9437d00b-bc2c-451c-9f74-77a99ec9e358
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
jay@jay-desktop:~$

---

### Post by DGortze380 on 2009-03-25
Yup, looks like you actually have two disks, with the same UUID and two installs of ubuntu.

Restart the computer.
If you get a message saying "Press Esc to Enter Menu", press Esc.
If not, the GRUB menu should come up.

Select the first option that says "Ubuntu 8.10" (or similar)
Note which 'Desktop' you are brought to.

Reboot, repeat above except this time select the SECOND option that says "Ubuntu 8.10" (or similar).

You should get the other desktop.

---

### Post by Saltwaterfishin on 2009-03-25
Thanks for all the help. 

Now that we have diagnosed the problem, how can I set the computer to only use the hard drive that has my preferred settings on it?

---

### Post by lykwydchykyn on 2009-03-26
Since you derive no benefit from having the two drives in there, figure out which one is the right one and unplug the other one.  Shut the computer off, unplug one of the drives, and boot.  If you get the desktop you want, you're good.  If not, shut it back down, unplug the other one instead, and boot.

Once you've figured out which is the one you don't want, pull it out and save it for a spare.  Or format it and use it for extra storage.  Just make sure you know for certain which disk is which.

---

