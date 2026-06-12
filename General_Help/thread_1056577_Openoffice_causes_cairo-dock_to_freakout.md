---
title: "Openoffice causes cairo-dock to freakout"
date: 2009-01-31
forum: General Help
---

### Post by Starman~ on 2009-01-31
I've been looking all over the web for this. Looks like I maight be alone here, hope not.

The problem is that cairo-dock functions well until I open openoffice. Then the graphics on the dock go bezerk when I move the mouse over the dock. The last time it happened I had to reinstall the dock because the entire background turned into a large black block, and couldn't be fixed. 

Oddly, its only with openoffice open, at all other times the dock seems to function well.

Is there something I have overlooked, or some tweak that needs doing? I am a noob and trouble shooting this is over my head. The only work around seems to be quiting or hiding the dock while writer is open, and then closing it before I access the dock.

---

### Post by Shmalignant on 2009-02-14
I'm experiencing the same problem here.  With OpenOffice writer or math open, when I hover the cursor over my ciaro dock, the dock glitches in and out of visibility with a rainbowy silhouette.  This same thing happens when I hover the cursor over the top window frame of writer and math.

In addition, it seems that OpenOffice writer crashes my visual effects at random.  When this happens, I have to change my visual effects back to extra while the system searches for my video driver.  This is quite annoying as I use writer often.

If anybody has any idea what could be causing this please post.  In the mean time I'll continue to search for a solution.

HP Pavilion dv6000
Ubuntu 8.10
NVIDIA GeForce Go 7400
Driver version 177.82
OpenOffice 3.0
Ciaro Dock 1.6.3.1

---

### Post by soldar79 on 2009-04-04
Hi there!

I'm using a HP DV6000. This is the profile

-Computer-
Processor		: 2x AMD Turion(tm) 64 X2 Mobile Technology TL-60
Memory		: 2007MB (504MB used)
Operating System		: Ubuntu 8.10
-Display-
Resolution		: 1280x800 pixels
OpenGL Renderer		: GeForce 7150M / nForce 630M/PCI/SSE2/3DNOW!
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA NVidia
-Input Devices-
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 USB Mouse
 Power Button (FF)
 Sleep Button (CM)
 Lid Switch
 Power Button (CM)
 Video Bus
 HP Webcam
 PC Speaker
 SynPS/2 Synaptics TouchPad
-Printers (CUPS)-
HP_LaserJet_1018		: <i>(Default)</i>
-IDE Disks-
-SCSI Disks-
TSSTcorp CDDVDW TS-L632N
ATA FUJITSU MHZ2160B

I've been trying to figure out how to get rid of the f***g issue of cairo-dock and openoffice.

I think I've solved it. I've edited the xorg.conf, and now it goes like this:


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option  "NvAGP"       "1"
#        Option "AddARGBGLXVisuals" "True"
EndSection

Since that, It SEEMS that cairo-dock is disappearing no more when using Openoffice 3.0. Hope you find this useful and let me know if it solved the issue.

---

### Post by Mason Whitaker on 2009-04-04
AWN is better, btw :P

---

