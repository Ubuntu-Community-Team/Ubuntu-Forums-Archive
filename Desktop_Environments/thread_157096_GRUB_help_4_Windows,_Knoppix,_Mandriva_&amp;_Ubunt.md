---
title: "GRUB help 4 Windows, Knoppix, Mandriva &amp; Ubuntu"
date: 2006-04-08
forum: Desktop Environments
---

### Post by pranav on 2006-04-08
I am new to Linux and hence i am trying out a lot of new distros

The major problem i face aftr every hd-install is the GRUB. 

I want to know if a grub installation cd exists.. such that i put the cd in .. it detects all the differnt operating systems i have installed n installs grub in MBR. is there such a cd ? So far only the Ubuntu install cd has the capability of detecting all the other Operating systems n installing a correct GRUB. but reinstalling ubuntu after every distro is not a practical solution, especially whn configuring ubuntu involves dwlding over 50 mb of codecs, multimedia tools, plugins,etc

i am not talkin abt installin grub on a cd or a floppy. Google searches have always given me such results. I want to install grub from the cd n not the other way.

Please help.

---

### Post by pranav on 2006-04-08
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php) is something i found called Super GRUB Disk

am dwlding it right now, will try it n let you know.... hopefully this is wht i want.. anything better that exists and you suggest ?

---

### Post by pranav on 2006-04-09
OK i tried it... 
it isnt what i was really looking for.. i still need somebody to suggest me a grub installation cd

which will detect all the different OS installed... just like the grub installer of UBUNTU does.. and then install the grub

Please help

---

### Post by Zar on 2006-04-09
I am looking for a solution to this too.  I installed Mandriva, dual booting with Ubuntu, Even though I used grub with Mandriva, it did not recognized Ubuntu.  I had to manually edit menu.1st file.  Not very convenient.

---

### Post by Irony on 2006-04-09
I personally just skip the install grub stage when trying out new distros. Its quite simple to manually edit the /boot/grub/menu.lst - for example here you can see that I just added the extra Breezy boots and the Zenwalk boot, I've also done the same on FC4.

Note that you just look at the kernel and initrid paths in the boot folder, and alter the root path to the appropriate partition;

[PHP]title		Breezy 5.10, hda2
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash vga=0x31A
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Breezy 5.10, hda2 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Breezy 5.10, hda2 (memtest86+)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry added by me for other Ubuntus
title		Breezy 5.10, hda6
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet splash vga=0x31A
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Breezy 5.10, hda6 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Breezy 5.10, hda6 (memtest86+)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
boot

title		Breezy 5.10, hdb3
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro quiet splash vga=0x31A
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Breezy 5.10, hdb3 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Breezy 5.10, hdb3 (memtest86+)
root		(hd1,2)
kernel		/boot/memtest86+.bin  
boot

# This entry added by me for an existing linux
# installation on /dev/hdb4
title		Zenwalk 2.01, hdb4
root		(hd1,3)
kernel		/boot/vmlinuz root=/dev/hdb4 ro
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		XP Home SP2, hda1
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/PHP]

---

### Post by louis_nichols on 2006-04-09
Unfortunatelly, when it comes to grub, there is no easy way out. My opinion is that, sooner or later, we all learn (wether we want it or not) how to do things the hard way. Which is actually not that hard, once you understand that it counts partitions from 0, whereas Linux starts with 1. :)

this thread might help, though.

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Sutekh on 2006-04-09
[QUOTE=Irony]I personally just skip the install grub stage when trying out new distros. Its quite simple to manually edit the /boot/grub/menu.lst - for example here you can see that I just added the extra Breezy boots and the Zenwalk boot, I've also done the same on FC4.[/QUOTE]
In my opinion this is the best way to do it too.  

I let the GRUB installed by Ubuntu take over the MBR.  With any subsequent OS I've installed (FC5, MEPIS), I instruct their installer to put their bootloader in the partition they are installed on not the MBR.  

All I have to do is copy the menu entry from each of the other menu.lst's into Ubuntu's one, and make sure that they point to the correct location.  A couple of commands to edit the files, and some copy and paste.

---

### Post by pranav on 2006-04-16
[QUOTE=louis_nichols]Unfortunatelly, when it comes to grub, there is no easy way out. My opinion is that, sooner or later, we all learn (wether we want it or not) how to do things the hard way. Which is actually not that hard, once you understand that it counts partitions from 0, whereas Linux starts with 1. :)

this thread might help, though.

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)[/QUOTE]


This is what i have done, its a matter of simply editing the menu.lst file in the grub folder. 

btw Simply Mepis Live CD has a good easy Grub installer, although it doesnt detect other distros of GNU/Linux.

---

### Post by louis_nichols on 2006-04-16
Glad you worked it out!

A simple thing that teaches you about how grub works is to use grub's command line to boot an OS. Just press 'c' when the grub screen shows up.

It's pretty educating and might save you some trouble in the future. Once, I changed the partition table without realising what that would mean to grub, so, although the data and disk was healthy, it wouldn't boot. In cases like this, it's useful to know the 2 or 3 commands grub needs to boot an OS. It is simpler than booting a livecd.

---

### Post by adrian15 on 2006-04-20
[QUOTE=pranav]OK i tried it... 
it isnt what i was really looking for.. i still need somebody to suggest me a grub installation cd

which will detect all the different OS installed... just like the grub installer of UBUNTU does.. and then install the grub

Please help[/QUOTE]

I've added this to the todo list of Super Grub Disk when it will be merged into a live cd system.

But I don't promise you anything in the short-term.

adrian15

---

