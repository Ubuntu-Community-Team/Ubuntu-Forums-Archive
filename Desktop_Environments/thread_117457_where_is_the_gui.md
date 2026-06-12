---
title: "where is the gui?"
date: 2006-01-14
forum: Desktop Environments
---

### Post by mgaski on 2006-01-14
i have tried to startx after login but all i get is lines of color flickering across the screen for a second or two and then my monitor goes into suspend mode.  alt-cntl-f1 shows me that certain fonts renderering is already registered at priority 0 and that client 6 rejected from local host.  this occurred right after installing.  i changed hostname from ubuntu to another name during install.  i am thinking that the video configuration isn't right somewhere.  i use a s3 trios 64v2-dx/gx video card.  what could be the problem?

---

### Post by stuporglue on 2006-01-15
I'd guess just a bad video configuration. Sounds like you're on the command line alright, so try this:

$ sudo dpkg-reconfigure xserver-xorg
(bunch of prompts...answer as best as you can)
$ sudo /etc/init.d/gdm restart

Repeat that until the graphics start, or you get board, but choose different options during the reconfigure part. It will generate a new xorg.conf for you, which will hopefully work correctly. 

Good luck

---

### Post by twigboy on 2006-01-15
also you can hit ctrl+alt+F1 to get to a terminal and try
sudo nano /etc/X11/xorg.conf

and you're looking for a section similar to this, except it wont have the savage stuff, it'll proly be generic.

Section "Device"
	Identifier	"S3 SuperSavage"
	Driver		"savage"
	VendorName	"S3"
	BoardName	"S3 SuperSavage/IXC 64"
	BusID		"PCI:1:0:0"

then look at the Driver and change whats in the quotes to vesa.  That a generic video driver.  Mine was originally set to nv.  When I switched it to vesa and rebooted it worked for me.

---

