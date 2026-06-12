---
title: "Video flicker problem with Jaunty  (no issues with Hardy)"
date: 2009-05-10
forum: General Help
---

### Post by yankeeDDL on 2009-05-10
Hello,

I have a clean install of Januty (new partition) and I have quite some issues with the video/graphics.
1) Whenever I launch Movie Player (Totem) the screen starts flickering and the CPU goes 100%.
Perhaps flickering is not the best term ... it's like it has a blank frame every few 'normal' frames. It's annoying as hell, but the worst part is 100% CPU load which almost locks the system.
If I manage to quit Totem, after a few minutes the flickering stops and everything goes back to normal.
2) The monitor's back-illumination never goes off. The screensaver kicks in, and the monitor goes blank when it should, but it never goes iin standby.

Some info that might help debugging:
a) In Hardy I had the issue with flickering, but I changed the viedo out to no-X11 and the flickering was gone for good.
b) If I use VLC instead of Totem, there's no issue.
c) I tried changing the options in gstreamer-properties. In the "Video" tab, I tried autodetect, "X windows system - no Xv" and "X windows system X11/....". All of them cause flickering with Totem.
d) I copy-pasted the xorg.conf from the Hardy install (it was the default, but I thought I'd try anyway): no changes.
e) I have also modified the xorg.conf as I saw in one of the websites: see at the bottom. You may notice a new section (ServerFlags).
It made no differences whatsoever.
f) I don't know if the flickering and the lack of standby are related.

Thanks in advance
- YankeeDDL


Section "Monitor"
	Identifier	"Configured Monitor"
        Option          "DPMS"
EndSection

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
	Driver	"fglrx"
EndSection
Section "ServerFlags"
        Option          "BlankTime"     "4"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "5"
EndSection

---

### Post by yankeeDDL on 2009-05-10
Forgot to mention the specs:
- Athlon 64 (I am using the 64bit versions of both Hardy and Jaunty)
- ATI Radeon HD2600XT
- 4GB of Ram
- MB: Asus A8N-VM (onboard Nvidia graphic chip is disabled by BIOS)

---

