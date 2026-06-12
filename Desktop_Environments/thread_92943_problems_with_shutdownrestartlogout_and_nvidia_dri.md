---
title: "problems with shutdown/restart/logout and nvidia drivers?"
date: 2005-11-20
forum: Desktop Environments
---

### Post by ren wins on 2005-11-20
since i installed the nVidia drivers (as well as a bunch of other random things i found in synaptic), every time i try to shut down or restart or even log out my computer freezes with a color noise pattern displayed. sometimes there's a repeating noise, but that's  ussually only when i dont shut down rythmbox.

i installed the drivers according to ubuntuguide.com, but that's based on hoary and im using breezy.  oh, i'm also using edubuntu

---

### Post by Snocrash on 2005-11-21
Had the same problem.

Fixed it by turning off the splash screen and setting vga=normal in my menu.lst in /boot/grub.

working fine since then.....


-Sno

---

### Post by ren wins on 2005-11-21
thanks, i'll give that a try

---

### Post by ren wins on 2005-11-21
there is nothing that says 'vga' in /boot/grub/menu.lst ?

and i had the splash screen turned off since i installed the drivers

---

### Post by gmosaihuate on 2005-11-21
I'm having the same problem too,

Laptop Dell Inspiron 2650
Nvidia GeForce2 Go 16mb
Pentium 4M  2.0 Ghz
512MB RAM
Using dual instalation linux/win2k 

Packages installed:
nvidia-glx 
nvidia-kernel-common
nvidia-settings
linux-restricted-modules-2.6.12-9-686
xserver-xorg-driver-nv

Installed nvidia drivers using steps according to Ubuntu 5.10 Starter Guide

/etc/X11/xorg.conf :
....
Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option  	"NoLogo"
EndSection
....


/boot/grub/menu.lst
....
title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,4)
kernel		/vmlinuz-2.6.12-9-686 root=/dev/hda7 ro quiet splash vga=normal
initrd		/initrd.img-2.6.12-9-686
savedefault
boot
....

Thanks in Advance
Gian

---

### Post by ren wins on 2005-11-22
i've still got the problem

i suppose a bit more detail would help
edubuntu 5.10
amd 2200 processor with 512mb ram
dual boot w/ windows XP
NVidia FX 5700 graphics card


i cant remember the packages i installed relating to the drivers? can someone give me an idea?

---

### Post by Heftiger on 2007-10-20
I have this same problem.

I have a Sony VAIO VGN-S460 with a nvidia GeForce Go 6200.

The shut down process worked fine until I installed the drivers. Ever since then I've had this strange problem. Whenever I shut down, or even log out, the screen seems to fade out in an odd way and then colored lines scroll the screen. Depending on how long I have had the system on, it sometimes does not last for a long time. However, if I've had my laptop on for a few hours, it takes a long time to shut down and sometimes freezes with the odd pattern displayed.

---

### Post by GaryParr on 2007-11-13
Happening here as well on Sony VGN S380 with GeForce Go 6200. I've tried everything I can think of and no joy. Rather annoying,

---

### Post by GoJa on 2007-11-19
I have a new Dell box with Feisty Fawn 7.04 and a nVidia 8300 GS.  I updated the nVidia drivers and things still worked, but lspci did not report my video card correctly (it said unknown hardware).  I did a post on the problem and was told to do sudo update-pciids.  This worked and lspci correctly reported my video card make and model.  But that is when my shutdown problems started.  The system would do what appeared to be all the normal shutdown things except the power would never go off.  The only way to shut it down completely was to hold in the power button for 5 to 10 seconds.

This link talks about this as a bug, but in an earlier version.  It appears as if the bug still exists.

[https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/46874](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/46874)

This link describes a work-around (it is referenced in the above bug report).  

[http://ubuntuforums.org/showpost.php?p=940244&postcount=34](http://ubuntuforums.org/showpost.php?p=940244&postcount=34)

I edited the file as described and my shutdown now works.

---

### Post by GaryParr on 2007-11-19
Actually, I think you have a different problem that the one we are experiencing. The hang-on-shutdown can be resolved by removing or disabling usplash. The "random noise" on shutdown cannot be resolved this way. The bug for the noise problem is

 [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/32389]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/32389") 

which can be corrected by reverting to the nv drivers (but you lose 3d rendering and will have issues with dual displays). For now, I'm suffering with the shutdown noise and the occasional manual power-off.

---

