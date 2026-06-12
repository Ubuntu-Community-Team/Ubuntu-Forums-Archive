---
title: "2 monitors, ATI, video playback stretched - only when using GDM"
date: 2006-08-28
forum: Desktop Environments
---

### Post by kaiwondergoo on 2006-08-28
ubuntu ver 6.06
ATI drivers (fglrx) x700pro / 'big monitor' setup (2 display)
totem
gxine
gnome
gdm


I have 2 (same) LCD screens connected to an ATI card. Both monitors work. 3D works (even running warcraft3 at 2560x1024). Xinerama is not used. Video playback is distorted (tested totem/gxine). Best technical term I know to use here is "it looks like it's stretching 4:3 video to 8:3". And for the kicker, this only happens if I log in from GDM. Running startx from a command line plays videos correctly (and everythign else works). I have reproduced the problem with my x700 and x1900xtx. 

Knowing nothing (yet) of GDM, I thought I would ask for some ideas here.

for reference - relavant info from xorg.conf:
```
Section "Device"
	Identifier	"x700[0]"
	Driver		"fglrx"
	Option		"DesktopSetup" "horizontal,reverse"
	Option		"OverlayOnCRTC2" "1"
	Option		"EnablePrivateBackZ" "yes"
	BusID		"PCI:5:0:0"
EndSection

Section "Device"
	Identifier	"x700[1]"
	Driver		"fglrx"
	BusID		"PCI:5:0:0"
	Screen		1
EndSection
```

Thanks in advance,
kwg

---

### Post by KenSentMe on 2006-09-28
I have the same problem here, only my xorg.conf looks like this: 

> 
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
EndSection


Totem is also stretched with this setup. Someone have an idea what to do?

---

### Post by peabody on 2006-09-28
> **KenSentMe said:**
> I have the same problem here, only my xorg.conf looks like this: 



Totem is also stretched with this setup. Someone have an idea what to do?

It's a known bug with the fglrx drivers.  There's lots of chatter about it over at the ati unofficial bugzilla.  I got around this problem by using mirror mode.  That's not so bad if you're on an LCD, but if you're on a CRT it'll limit you to a flickering, headache-inducing 60Hrz.  Your resolution may be even more limited depending on what the tvout on your particular ati card can handle.  I didn't know about getting around it by not using gdm, that's a nice tip, thanks.

---

### Post by kaiwondergoo on 2006-09-28
> **KenSentMe said:**
> I have the same problem here, only my xorg.conf looks like this: 



Totem is also stretched with this setup. Someone have an idea what to do?

I decided to updade the drivers to see if I could get a game to work. The game still crashed out, but the video problem fixed. So I can confirm that it's a bug with the ati drivers.

Shortly after that I got rid of my x1900xtx and bought a nVidia 7950. Everything works now and I am much happier for it.

---

### Post by KenSentMe on 2006-09-28
> **kaiwondergoo said:**
> I decided to updade the drivers to see if I could get a game to work. The game still crashed out, but the video problem fixed. So I can confirm that it's a bug with the ati drivers.

Shortly after that I got rid of my x1900xtx and bought a nVidia 7950. Everything works now and I am much happier for it.

Well, games work fine here, but i was already thinking about buying a nVidia card. Things are much easier with nVidia.

---

