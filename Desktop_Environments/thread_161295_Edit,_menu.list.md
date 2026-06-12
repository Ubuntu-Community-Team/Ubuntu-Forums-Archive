---
title: "Edit, menu.list"
date: 2006-04-16
forum: Desktop Environments
---

### Post by majkmil on 2006-04-16
My /boot/grub/menu.list file has about six or seven different kernels. I am using the 2.6.12-10-686 kernel. I am running a Athlon 2000+ CPU, with a gig of ram and a 80Gb HD. Is this the best kernel for this platform? I was wondering why I have all these other kernels in mt list. Can I delete them? Should I delete them? One reason I am asking is, when I get updates it wants to update all the other kernels. Any help is appreciated. Here is my list.

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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


title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-686



title		Ubuntu, kernel 2.6.12-custom 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-custom root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-custom
savedefault
boot

title		Ubuntu, kernel 2.6.12-custom (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-custom root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-custom
boot

title		Ubuntu, kernel 2.6.12-10-k7-smp 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7-smp root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-k7-smp (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7-smp root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-k7-smp
boot

title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-k7
boot



title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-686-smp 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-686-smp root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686-smp (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-686-smp root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-686-smp
boot

title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-686
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by aysiu on 2006-04-16
Go to System > Administration > Synaptic Package Manager.
Search for the word *linux-image* and mark for uninstall all the ones you don't want.
Then, click Apply.

---

### Post by majkmil on 2006-04-16
Can you recommend which ones I should keep? Is the 686 kernel the best for my system? Thanks

---

### Post by aysiu on 2006-04-16
[QUOTE=majkmil]Can you recommend which ones I should keep? Is the 686 kernel the best for my system? Thanks[/QUOTE] I'm not 100% sure, but I believe for AMD Athlon, you should use the k7 kernel.

---

### Post by majkmil on 2006-04-16
thats what I thought, but I read that the 686 might be faster. It could be my imagination. Should I just keep the others?

---

### Post by aysiu on 2006-04-16
[QUOTE=majkmil]thats what I thought, but I read that the 686 might be faster. It could be my imagination. Should I just keep the others?[/QUOTE] I would try booting into each one, seeing how it affects your system, and keep the one that works best.

I have an AthlonXP, and it behaves just about the same, no matter what kernel I use, but people have told me k7 is specifically for AMD processors.

---

