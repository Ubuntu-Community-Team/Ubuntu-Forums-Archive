---
title: "Problems with gnome"
date: 2008-10-10
forum: Desktop Environments
---

### Post by collinge on 2008-10-10
i think i installed a corrupted desktop theme. When i login i get a black screen with a terminal... nothing else works... i have tried the code: gconf-2 - - recursive-unset /apps/panel .... but nothing seems to work... any ideas?

---

### Post by collinge on 2008-10-13
i have also tried mv ~/.gnome2 ~/.gnome2.old ... it does nothing

---

### Post by brianfreytag on 2008-10-13
Which flavor of Ubuntu is this?
What are your system specs?
What is in your xorg.conf
```
cat /etc/X11/xorg.conf
```

Let us know these things and will try to help.

---

### Post by collinge on 2008-10-13
i am using 
Ubuntu 8.04 - the Hardy Heron on a Dell 4600 
and gnome v 2.22.3




Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by brianfreytag on 2008-10-13
Can you boot into the fail safe option in the Grub menu?

What graphics card does that computer have?

**Added Below**

Try running

```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

This will reconfigure your xserver, and may fix it.  Let me know how it goes.

---

