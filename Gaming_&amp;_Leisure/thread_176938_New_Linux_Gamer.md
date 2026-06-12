---
title: "New Linux Gamer"
date: 2006-05-15
forum: Gaming &amp; Leisure
---

### Post by z3snap on 2006-05-15
I'm new to Linux gaming, and need to know all the programs I need to install as a prerequisite to gaming on Linux... I install the UT2004 demo and this error came up: ```
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History:

Exiting due to error

```

---

### Post by glotz on 2006-05-15
What 3D card do you have got? Have you installed any drivers for it? (just guessing here...)

---

### Post by z3snap on 2006-05-15
sry, I have an ATI Radeon 9200se, I downloaded the new driver but not sure if it is installed...

---

### Post by R3linquish3r on 2006-05-15
[QUOTE=z3snap]sry, I have an ATI Radeon 9200se, I downloaded the new driver but not sure if it is installed...[/QUOTE]

Open your terminal and do
fglrxinfo

if it says Mesa Project then the driver is not running.

Open the terminal and put 
sudo gedit /etc/X11/xorg.conf

Scroll down till you find this:

Section "Device"
	Identifier	"Your ATI Card"
	Driver		"mesa"
	BusID		"PCI:1:0:0"
EndSection

change the "mesa" to "fglrx" and reboot. you shud be good to go.

---

### Post by z3snap on 2006-05-17
thx it works great :-D

---

### Post by leech on 2006-05-17
[QUOTE=R3linquish3r]Open your terminal and do
fglrxinfo

if it says Mesa Project then the driver is not running.

Open the terminal and put 
sudo gedit /etc/X11/xorg.conf

Scroll down till you find this:

Section "Device"
	Identifier	"Your ATI Card"
	Driver		"mesa"
	BusID		"PCI:1:0:0"
EndSection

change the "mesa" to "fglrx" and reboot. you shud be good to go.[/QUOTE]

Shouldn't that be "vesa" instead of "mesa" in xorg.conf?  

Leech

---

### Post by R3linquish3r on 2006-05-17
[QUOTE=leech]Shouldn't that be "vesa" instead of "mesa" in xorg.conf?  

Leech[/QUOTE]

Vesa or mesa, it depends really. I beleive mesa is used in the 9000 series and vesa is used in the x000 series

---

