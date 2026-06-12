---
title: "NVIDIA doesn't work at all"
date: 2006-03-03
forum: Desktop Environments
---

### Post by excelsior on 2006-03-03
Hi all
I need to run blender, but my NVIDIA isn't working at all.
I tried the steps outlined in a few other threads and howtos, but every time I change my xorg.conf file like I need to my X window system crashes.

in my xorg:

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

I need to change the Driver to "nvidia", but it crashes when i try.
Help?

---

### Post by Iandefor on 2006-03-03
Have you tried 
> 
sudo dpkg-reconfigure -phigh xserver-xorg It's seriously missing what hardware you actually have running. And, to be doubly sure, do you have the driver you need installed?

---

### Post by KansasJoe on 2006-03-03
switch ur BUS ID to "PCI:1:0:0"  -that's what finally got it working for me

---

