---
title: "Weird freeze on Linux distros"
date: 2006-08-19
forum: Desktop Environments
---

### Post by goldencako on 2006-08-19
Hey, I have recently installed Ubuntu with no problem at all. The only thing is that sometimes, all of a sudden, the mouse clicks and keyboard stops working (the mouse can still move) and colored vertical lines appeared all over my screen. This also happens when i let it sit for a while with only the screensaver. The only way to solve that is by restarting. This had happened several times with SuSE 9.3 and I wasn't able to fix it. Hope anyone can help. Thanks

---

### Post by cptnapalm on 2006-08-19
Sounds like a hardware problem (possibly driver related?)

What video card and driver are you using?

---

### Post by jordilin on 2006-08-19
take a look at system logs as well, located in /var/log/messages and paste relevant info.

---

### Post by goldencako on 2006-08-19
This is wut it said on xorg.conf (I don't know where else to find that info).

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

I thought it might be a harware problem but I have double boot nothing even similar has happened while I'm running XP. The funny thing is it happened both on SuSE and Ubuntu... maybe they both configured my video card wrong. I looked all over the log but I couldn't find anything relevant... the log entries that should be there at the time it froze were probably not save due to the crash. It happened again today like an hour ago, but this time not lines, just weird coloring in some parts of the screen. One could almost not noticed it had frozen because the screen was almost the same and mouse still moved. very weird

---

### Post by goldencako on 2006-08-20
so no light on the subject until now? i has happened twice again :(

---

### Post by kerry_s on 2006-08-20
Well since your not using the proprietary nvidia drivers, try changing to the vesa drivers.

Driver "nv"

to

Driver "vesa"

ctrl+alt+backspace to restart x

if that don't work try the proprietary nvidia drivers

sudo apt-get update <then> sudo apt-get install nvidia-glx

and change the xorg.conf to 

Driver "nv"

to

Driver "nvidia"

ctrl+alt+backspace to restart x

---

### Post by goldencako on 2006-08-21
Thanks a lot. I tried the first option, changin 'nv' to 'VESA', so I'm gonna just gonna wait and see if it happens again. If it does I'll try the second option.

---

