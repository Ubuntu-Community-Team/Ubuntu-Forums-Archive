---
title: "[SOLVED] kdm blocks loging out/shutdown"
date: 2008-05-21
forum: Desktop Environments
---

### Post by pixel :-) on 2008-05-21
I'm under kde3 8.04 64 bit(i don't think it's related,i'm trying here first).At shutdown, and logout.It hangs systematicly, i have to press ctrl alt del to continiou shutdown.Kde is closed normally, but then blocks when the screen is black,ctrl alt back space doesn't work and num lock is blocked.For know i'm surviving with gdm that works fine.

with fglrx "RADEON X600 Series"

i think i had this in the past, and the sollution was to fix something in the xorg fille.Here's my xorg file ,any ideas?Also the default xorg fille didn't work at all, this one is a little bit changed.


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by takowl on 2008-05-21
I think it's something to do with fglrx...I had the same problem in KDE4. Have a look at [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/118605/comments/32](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/118605/comments/32) , which has solved the same problem for several people, myself included.

Thomas

---

### Post by pixel :-) on 2008-05-21
Worked for me too.Thank you takowl :guitar:

---

