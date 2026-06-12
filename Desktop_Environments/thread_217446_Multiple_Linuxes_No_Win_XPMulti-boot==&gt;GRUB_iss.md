---
title: "Multiple Linuxes: No Win XPMulti-boot==&gt;GRUB issues"
date: 2006-07-17
forum: Desktop Environments
---

### Post by shuttleworthwannabe on 2006-07-17
Hi There

I have a laptop that I am dedicating to Linux only. And so far I have 6 partitions on the HDD.
Primary HDD: hda1 (Ubuntu Dapper)
Logical HDD: hda5 (Kubuntu Dapper), hda6 (Xubuntu Dapper), hda7 (MEPIS 6), hda8 (unallocated), hda9 (unallocated), hda10 (linux-swap).
The drive was formated for linux file systems (all reiserfs)
I started by installing Kubuntu on hda5 using text mode, but did not get a option where to intall GRUB, so it defaulted to MBR (on hda1). I then installed Ubuntu on hda1, chose to put the GRUB on MBR and it recognised the Kubuntu and listed this in GRUB. Next I installed xubuntu (did not have text mode, only LIVEcd version); but did not have option for GRUB installation (defaulted to MBR as well, overwriting the Ubuntu; recognised the Ubuntu and Kubuntu install and listed in the GRUB).
Because MEPIS allows me to choose the place where to install GRUB, I chose to put the MEPSI grub on hda7. 

Here is what I ideally want:
Use Ubuntu Grub to boot into the other Linuxes, i.e. enter chainloaders in Ubuntu GRUB to boot into respective Linuxes. I would like to install the respective GRUB's onto /root of the respective hda's.

How do I go about doing this?

Here is what I have thought about (after seeing a number of suggestions here and elsewhere):
1. Boot into Ubuntu (hda1) and reinstall GRUB from here: [COLOR=Red]$ sudo grub-install /dev/hda [COLOR=Navy]#<---is this correct???[/COLOR]
[COLOR=Black]While here make chainloader entries in the menu.list file for the other OS, is this correct?[/COLOR]
[COLOR=Black]2.  Once it loads the GRUB there (MBR), I will be allowed to choose  which other Linux OS I want to boot into (hopefully it recognized other OS installed on the hda); I boot into the respective partitions and  while in there, re-install grub on ther /root partitions of the respective OS. Is this right?

Can someone please guide me before I make a mess of this?

Much appreciated,
swb
[/COLOR][/COLOR]

---

### Post by Tamihania on 2006-07-17
Hi swb,

I am personally interested in the 'pro's' answer for your questions :) and I subscribed to your thread. I wanted to make similiar things in the past and unfortunately had too less patience and time to go through it on my own...didn't have courage enough to ask for help either...

Anyway - I have some materials to read on the subject if you have enough time (I did not!...lol):
Here they are:

[GNU GRUB]("http://www.gnu.org/software/grub/manual/grub.html")

[Grub howto]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/HOWTO_GRUB_BOOTLOADER_AND_TROUBLE_SHOOTER")

I am sorry not to be of a better help - but - I will try to help you to bump if needed :)

tami

---

### Post by ajgreeny on 2006-07-17
So you have a grub menu at the moment that lets you boot into all your linux OS's, is that correct?  Or do you need to set the bios to boot from a different disk for a mepis bootup?

Aside from all that I found the easiest way was to make sure I had a copy of all the relevant entries on the menu.lst file in my MBR and then install Mepis grub on the MBR.  If I remember right, it found all my other linux OS's and added them to the menu.lst of mepis. If it didn't I silmply had to add the appropriate entries to the mepis grub.  I then booted into ubuntu and did the same thing the other way round, ie added the mepis entry into the ubuntu grub menu.lst.

Anyway, the really easy thing to tell you is that provided you keep a copy of the required entries for the OS's you may want to add to grub, where-ever you chose to put it, it is very simple to edit the grub menu.lst accordingly, and then boot to your chosen distro.

I hope this all makes sense, but if not come back again with more detailed questions and I'll see what help I can give you.  Good luck.

---

### Post by shuttleworthwannabe on 2006-07-17
```
title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-23-686 (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-23-686 (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-23-686 (on /dev/hda5) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-23-686 (recovery mode) (on /dev/hda5) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda5 ro single 
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, memtest86+ (on /dev/hda5) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Ubuntu, kernel 2.6.15-23-686 (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Ubuntu, kernel 2.6.15-23-686 (recovery mode) (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda5 ro single 
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Ubuntu, memtest86+ (on /dev/hda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

This what my current menu.lst looks like. It is taken from the Xubuntu /root/boot/grub/ folder.  And yes, I can see and boot into all the the other OS in this menu.lst (except for MEPIS, because I have installed its grub in the MEPIS /root partition).

How do I make the Ubuntu on hda1 create a grub on MBR that would have all other OS in its menu.lst. Currently Xubuntu is "driving" the MBR grub, I want Ubuntu on Promamry parition to drive the GRUB menu. Then I want to install other OS's GRubs on their respective /root partitions. In this way I can minimise the clutter in the master menu list (i.e. Ubuntu grub menu list).

Here is a example of what I see it should let me do:
MBR should have Ubuntu's GRUB menu
with entries (default) to Ubuntu
then I will add chainload entries to this list so that I can boot into other OS. Once I boot into other OS, I will be confronted by another menu list where I can choose which kernel version to boot into.

I hope this is clear enough. I can explain further if necessary.

Many thanks for the above 2 replies.Much Appreciated,
swb

---

### Post by ajgreeny on 2006-07-17
OK I see what you want but I'm afraid I don't really know how you can do what you want.

I still think however, it is easiest to just make a note of the various entries on each OS's grub menu.lst and then transfer them all to the grub menu.lst of ubuntu, changing the order if you want.  If you're really worried about a large list showing at boot time you can always comment out some of the listed entries with a # at the start of the line marked "title" that you don't want to show.  That way you can have several OS's with just the primary kernel listed for each and you can even remove all the "recovery" entries except for the main ubuntu one.  What is your reason for wanting the grub on separate partitions for each operating system.  I'm not even sure how you get to boot into each one if you have separate grubs, as the computer will always try to start on the MBR, ie hd0,0.  I think if each was on a separate disk you could do it more easily but perhaps I just don't understand this chainloading business.

Sorry if this is very longwinded and still doesn't answer your question but I think it is worth thinking about my way.  Good luck to you in your search for info on this.

---

