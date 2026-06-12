---
title: "Grub help"
date: 2006-08-14
forum: Desktop Environments
---

### Post by njzillest on 2006-08-14
I first installed Ubuntu on my HD as /dev/hda1
Then i installed auditor as /dev/hda3

It seems as auditor overwrote the MBR. Ubuntu is still on the system, and im able to access it through auditor.

How can i change the grubs settings?
WHere is the textfile for the grub located? what should i put in the textfile?

Thanks for the help

---

### Post by PathSpace on 2006-08-14
I'm pretty sure that the text file is /boot/grub/menu.1st, but I don't know what exactly to tell you about modifying it...

---

### Post by Ramses de Norre on 2006-08-14
menu.**l**st =)
You can reinstall grub if you like, do you now load ubuntu through a bootloader that came with auditor or through the auditor live cd?

---

### Post by njzillest on 2006-08-14
What should i add so the grub recognizes Ubuntu?

This is my /boot/grub/menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue
gfxmenu (hd0,2)/boot/message

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro ramdisk_size=100000 lang=us apm=power-off nomce noapm vga=791

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

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

## ## End Default Options ##

title		Debian GNU/Linux-- Auditor
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/hda3 ro ramdisk_size=100000 lang=us apm=power-off nomce noapm vga=791 
initrd		/boot/initrd.img
savedefault
boot

title		Debian GNU/Linux, kernel 2.6.11-auditor-10 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.11-auditor-10 root=/dev/hda3 ro ramdisk_size=100000 lang=us apm=power-off nomce noapm vga=791 
initrd		/boot/initrd.img-2.6.11-auditor-10
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by bernied on 2006-08-14
You need another entry like the ones at the bottom of the file:
```
title		Debian GNU/Linux-- Auditor
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/hda3 ro ramdisk_size=100000 lang=us apm=power-off nomce noapm vga=791 
initrd		/boot/initrd.img
savedefault
boot
```
but you need to replace some of the options on the right-hand side:

title - just a label, anything you like (I suggest Ubuntu)

root - the location of the kernel and initrd files (the boot partition) - hopefully this is not the same place as your auditor install, or you might have some trouble

kernel - the name of the file that contains the kernel - if you haven't messed with the system too much this should be the same (vmlinuz). Also on this line are your kernel options. The most important of these is root=/dev/hdxx which is the location of your root filesystem (the / partition). Again, this should be different from your auditor install, else there will be trouble. Try using the options that I use below as well (ro is read-only, quiet is don't-give-me-lots-of-boot-messages and splash is that pretty boot screen ubuntu gives us).

initrd - this is the name of the file that contains your init ramdisk image, which is a basic set of files, modules and other bits that the kernel needs to get started. It will probably still be called initrd.img.

savedefault - this just means that if you boot this option, then it should be the default next time you boot. You can leave it out if you like.

boot - just go. This is also not necessary but it looks good.

Here's an example of my Kubuntu menu.lst (but even this is not standard because I've messed with it). Remember your partitions are probably different.
```
title           Kubuntu 2.6.15-26-686
root            (hd1,1)
kernel          /vmlinuz-2.6.15-26-686 root=/dev/hdb5 ro quiet splash
initrd          /initrd.img-2.6.15-26-686
boot
```

So, you need to know where you put that ubuntu distribution, and you need to convert that to grub terminology. Grub uses numbers and starts counting at 0, so (hd0,0) is /dev/hda1.

If you have trouble, post what you get from ```
fdisk -l
```
Also, you should know that if you go back to using ubuntu, the next time you upgrade your kernel, your auditor options will get wiped. To keep them, you need to move them to below where it says 
END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by njzillest on 2006-08-14
thanks alot man :-)

---

### Post by bernied on 2006-08-15
No prob, but I think I was wrong about Ubuntu messing up your Auditor settings. I think what would actually happen is that a kernel upgrade will mess up your Ubuntu boot options. This is because of these lines:
```
### BEGIN AUTOMAGIC KERNELS LIST
# kopt=root=/dev/hda3 ro ramdisk_size=100000 lang=us apm=power-off nomce noapm vga=791
# groot=(hd0,2)
```
This section of the file tells the grub-updater (which runs when you install a new kernel) what options to add to a new kernel (kopt), and where to find new kernels (groot). These are both wrong for your ubuntu kernels, because it's currently saying that the kernel should mount / and find the kernels in /dev/hda3

So (in my opinion), it would be best to fix those two lines, so they say something like:
```
# kopt=root=/dev/hda1 ro quiet splash
# groot=(hd0,0)
```
And maybe change this line as well
```
# alternative=false
```
so it's TRUE instead of FALSE
(this will give you the recovery mode option as well - but not until you upgrade your kernel, which is when you're most likely to need it).

At the very least, if you can't be bothered with doing this, make a backup copy of your menu.lst.

---

### Post by njzillest on 2006-08-16
I accessed my ubuntu HD through Auditor and just copied its part of the grub into auditors file.

But thanks alot for the help man :-D

---

