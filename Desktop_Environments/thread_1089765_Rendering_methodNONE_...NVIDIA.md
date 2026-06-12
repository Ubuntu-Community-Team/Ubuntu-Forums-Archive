---
title: "Rendering method:NONE ...NVIDIA"
date: 2009-03-07
forum: Desktop Environments
---

### Post by darco on 2009-03-07
Ok,getting frustrated here....I was running nvidia 180.35 just fine. Saw that .37 came out...did the basics upgrade steps, but ran into low graphics etc....tried allot of steps from reading other posts...
Nvida-setting is saying I dont have the drivers installed, need to run nvdia-xconfig as root,  Hardware drivers says I have proprietary drivers installed (180)....compiz check shows:

Gathering information about your system...

 Distribution:          Linux Mint 6
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8800 GT (rev a2)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

xorg-file:

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

the xorg file did say nvdia a couple of reboots ago so I dont know whats happening...
thxs for your help
darco

---

### Post by darco on 2009-03-07
after more wasted time, I was finally able to manage to get everything back to normal w/180.37.  I noticed the xorg.conf.new file was dumped in my home directory, after copying it over the current xorg file , everthing is fine..

arrgh... :confused:

darco

---

