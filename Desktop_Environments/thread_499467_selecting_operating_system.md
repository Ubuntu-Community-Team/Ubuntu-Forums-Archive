---
title: "selecting operating system"
date: 2007-07-12
forum: Desktop Environments
---

### Post by gamelord12 on 2007-07-12
I just installed Ubuntu where XP used to be, but now I can't access Vista.  I can browse to all of its files, so I know it's still there, but I can't boot to it.  How can I choose whether to boot to Ubuntu or Vista, like I used to with XP and Vista?

---

### Post by maybeway36 on 2007-07-12
You need to go into /boot/grub/menu.lst and add a Vista option. You should use the "chainloader" command. What partition of what drive is Vista on?
You should add something like this to menu.lst:
```
title Windows Vista
               rootnoverify (hd1,0)
               chainloader +1
```
The first number after "hd" is the drive (first drive is 0.) The second number (after the comma) is the partition number (first partition on the drive is 0.)
If this doesn't work, post back with your drive/partition layout.

---

### Post by gamelord12 on 2007-07-12
It says that the file is read-only, and it won't let me save because it says I'm not the owner of the file.  I have to go to work at the moment, but I'll be back around 11:00pm EST.  Here's what I've got and what I want to do:

two partitions; first volume Ubuntu, second volume Vista

allow 30 seconds to choose an OS, if none are chosen, default to Vista.  Also, if there's any way I could use my old boot screen (the one that VistaBootPro/BCDEdit modifies), I'd prefer that one so I could modify my boot settings within a GUI.  Thanks a lot, btw.

---

### Post by maybeway36 on 2007-07-12
First of all, log in and press Alt+F2. Type
```
gksu gedit /boot/grub/menu.lst
```
in the box. Find the line that begins with "default" and make it say this:
```
default	0
```
Find the "timeout" line and make it this:
```
timeout	30
```
If there is a line saying
```
hiddenmenu
```
change it to
```
#hiddenmenu
```
Scroll down to where it says
```
### BEGIN AUTOMAGIC KERNELS LIST
```
Right above that, put
```
title Windows Vista
 	rootnoverify (hd0,1)
	chainloader +1
```

Unfortunately, there is no way to get Windows Vista's boot menu to boot Ubuntu. Microsoft doesn't really like Linux all that much :P
If the steps are too confusing, just post your entire menu.lst and I'll edit it.

---

### Post by gamelord12 on 2007-07-12
I followed your directions exactly but it doesn't actually boot to Vista.  It just stays at a screen saying "Starting up...".  Here's my code though, if you want to double-check.

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
timeout		30

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

title Windows Vista
 	rootnoverify (hd0,1)
	chainloader +1

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
# kopt=root=UUID=873f4dc3-bced-4ad0-bafd-d6beca8c1b58 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=873f4dc3-bced-4ad0-bafd-d6beca8c1b58 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=873f4dc3-bced-4ad0-bafd-d6beca8c1b58 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

To change the Ubuntu options to something more pleasing to the eye, I can just change what's after the word "title", right?

---

### Post by gamelord12 on 2007-07-12
Okay, after applying updates, the boot screen now has two new choices, but rather than the kernal saying kernel 2.6.20-15-generic, the two new choices say kernel 2.6.20-16-generic.  Does that give me the option to boot to an non-updated Ubuntu?  Just wanted to add that before you got back to me on my problem with accessing Vista.

---

### Post by yatt on 2007-07-13
What is your partition layout? use gparted if you don't have it memorized)

---

### Post by gamelord12 on 2007-07-13
Could someone give me instructions for how to install GPartEd?  It was on the Live Ubuntu CD, but it's not in the regular OS.  I went to the site, and downloaded the compressed folder, but what do I do with it after I extract it?

---

### Post by maybeway36 on 2007-07-13
Getting all your Ubuntu software throught APT will save you a lot of headaches.
You can install gparted with Synaptic Package manager or go in a terminal and type
```
sudo aptitude install gparted
```
The multiple Ubuntu options on the boot menu mean that yes, you can run a downgraded Ubuntu. This is in case the new kernel doesn't work, so you can still run your system. I've never needed to use an old kernel, though.
As for Vista, I think maybe it put its bootloader in the XP partition, like XP does with 98. Since that's gone, you might need to reinstall from scratch :(
If you do, install Windows first, then Ubuntu. And if you need to get to your Vista partition for backups and can't, try booting Knoppix.

---

### Post by gamelord12 on 2007-07-13
I typed that in and it said it was setting up GPartEd (it must have finished because it didn't tell me it was doing anything after that), yet I can't access it.  Also, where's that package manager thing located?  I don't seem to have it.  And since all my Vista files are still in-tact and perfectly accessible by browsing from Ubuntu, is it safe to assume that it's still possible to boot to it in some way without re-installing?  Also, not that you guys aren't helpful (I really appreciate your help thus far) but is there a faster place for me to get help, like maybe a toll-free phone number or an instant message chat with someone?  Again, I'm on my way to work and I won't be able to call or IM anyone about it this second, but I'd like to get back to Vista because that's sorta where my life is.  I put every week's work schedule on Outlook, sync that to my iPod (as well as download the newest podcast from Gamespot), play all my favorite PC games, and video chat with my friends over AIM.

---

### Post by gamelord12 on 2007-07-13
Okay, it took a little while, but I found GPartEd.  I opened it up, and it looks like Vista is on the 5th partition?  I did resize some stuff a few different times, but did it really get named the 5th volume?  Is that where my trouble lies?  Based on that screenshot, what do you guys suggest?

[[IMG]http://img354.imageshack.us/img354/2405/mypartitionsif3.th.png[/IMG]](http://img354.imageshack.us/my.php?image=mypartitionsif3.png)

---

### Post by jessi3k3 on 2007-07-14
> **maybeway36 said:**
> Unfortunately, there is no way to get Windows Vista's boot menu to boot Ubuntu. Microsoft doesn't really like Linux all that much :P
If the steps are too confusing, just post your entire menu.lst and I'll edit it.

That's not true. I actually pulled it off. I'm using vista's boot menu to boot vista, xp pro, and ubuntu 7.04. I used EasyBCD to pull it off.

---

### Post by Computer Guru on 2007-07-14
Here you are: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by gamelord12 on 2007-07-14
Alright, I tried switching the hd(0,1) to hd(0,4) and after that didn't work, hd(0, 5).  No luck.  Any other ideas, guys?  I'd rather not waste money by taking it to Geek Squad or a place like them.

---

### Post by gamelord12 on 2007-07-14
Alright, I'm getting kinda desperate: I want Vista back.  If I deleted my other partition (and the one labeled "extended"...see my GPartEd screenshot in this thread), would it boot straight to Vista as if it were my only OS again?  Or at least show the boot loader that I had before with Vista as the only working option?

---

### Post by Computer Guru on 2007-07-15
No, it wouldn't.

You need to boot from the Vista DVD and repair your MBR. Or if you can boot into Vista now, use EasyBCD |
 Bootloader Management | Reinstall Vista Bootloader

---

### Post by gamelord12 on 2007-07-15
I can't boot into Vista.  I put in the Vista DVD and it said it couldn't auto-repair it.  How do I do it manually, step-by-step?

---

### Post by maybeway36 on 2007-07-20
I don't think you can boot Vista. It put its bootloader in the XP partition which is now gone. I would suggest wiping the hard drive and then installing Vista, then Ubuntu./

---

### Post by Computer Guru on 2007-07-22
Actually, Ubuntu then Vista would be better.

---

### Post by maybeway36 on 2007-07-22
> **Computer Guru said:**
> Actually, Ubuntu then Vista would be better.

How would you boot Ubuntu afterwards?

---

### Post by Computer Guru on 2007-07-24
By adding an Ubuntu entry to the Vista bootloader with EasyBCD.
It's made really easy with the new grubless-Linux option in the [1.61 Betas]("http://neosmart.net/forums/showthread.php?t=642").

---

### Post by darksidedude on 2007-07-24
I've read up on this issue, although i dont know how to fix it, Vista doesn't play well with linux (go figgure:) )
they use a new type of bootloader (grub is still better) but insted of boot.ini its a type of .exe file srry :(

---

