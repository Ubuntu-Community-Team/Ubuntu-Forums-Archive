---
title: "Logitech Tackball flakiness"
date: 2007-02-25
forum: Desktop Environments
---

### Post by wookie_bw on 2007-02-25
I have searched high and low and tried a few different things to no avail. I have a new install of Edgy and my Logitech 3 button trackball is having issues. It will randomly freeze until I reset the ball and it will just start jumping around in small incrementsm both at rest and when using it. 

I found a couple of things: I edited the kernel line in Grub, as some people found this to work, but it didn't help. I used noapic irqpoll pci=routeirq

I also tried changing some things in /etc/X11/xorg.conf, namely
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/**mouse0**"
	Option		"Protocol"		"**auto**"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

The bold parts are changed. Originally they were mice and ExplorerPS/2 I believe.

This happened in Breezy, Dapper and Edgy. The funny thing is, that awhile ago when I first installed Breezy it worked fine, if I remember correctly. But I reinstalled Breezy then upgraded to Dapper and finally a clean install of Edgy all yesterday and had this problem. The trackball works fine on my WinMCE laptop so the hardware is good.

Oh, and I have an NVidia graphics card. I saw some problems similar to mine from people with ATI.

Thanks for any help or insight.

-Brandon

---

