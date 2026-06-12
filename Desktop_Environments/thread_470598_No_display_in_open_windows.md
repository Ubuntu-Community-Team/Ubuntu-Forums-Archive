---
title: "No display in open windows"
date: 2007-06-11
forum: Desktop Environments
---

### Post by la_dolce_vita on 2007-06-11
Hello all,

This is my first post after one week in using Ubuntu 7.04. I've been unsuccessful in finding any references to this problem. Everything seems to be working, except for this annoying problem that pops up. 
After using Ubuntu (e.g. browsing the net, downloading emails, using word processor etc), I log off. After a few hours I come back and log back on.  It doesn't matter what window I open, whether it be my home directory, start evolution, firefox or any other window, the windows open blank i.e. no icons or fonts or anything else. Just   a border with the window buttons in the top right corner. Logging off and on does not fix the problem. However when I restart, all is fine. It seems while I'm working everything works great. The problem arises when the computer is left to idle even after logging off.

Hardware
Amd Athlon XP 1800
ATI Radeon 9250, but this is what's in the xorg.conf file
Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:2:0:0"
EndSection 

Maximum resolution possible on my system is 1024x768 @ 60 Hz

For my purposes, the screen res' is fine. Could it be the ACPI management system?

Thanks in advance,

R

---

### Post by renzokuken on 2007-06-11
not sure what the problem is but it almost definately stems from your xorg.conf.

do you have beryl or anything running? 

might be worth trying the "radeon" driver instead, or even "vesa".

also, a way to restart X without rebooting is to press Ctrl+Alt+Backspace

---

### Post by la_dolce_vita on 2007-06-12
I haven't installed Beryl, however I will try the open source ATI drivers if not the 'Vesa' drivers. Thanks for your suggestions.

cheers

---

