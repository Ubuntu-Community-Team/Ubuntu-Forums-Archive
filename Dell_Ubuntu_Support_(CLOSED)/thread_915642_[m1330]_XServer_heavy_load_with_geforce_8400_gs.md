---
title: "[m1330] XServer heavy load with geforce 8400 gs"
date: 2008-09-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gregstar on 2008-09-10
Hi guys!

I have a little problem here - a few days ago I recognized a heavy cpu load, but gnome-terminal didn't show me the causer. But htop showed that the XServer uses all of the cpu.

So I reconfigured XServer with dpkg-reconfigure, because I think I had damaged my xorg.conf. For a few minutes I thought that was the problem, but after starting some applications like Firefox or Thunderbird - the load goes up causing by X.

This is really annoyingly, because this decreases the running time on battery.

Here my xorg.conf:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	BusID          	"PCI:1:0:0"
#	Option    	"OnDemandVBlankInterrupts" "True"
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
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by sdennie on 2008-09-10
Does the X server go to 100% and stay there or does it just go up to 100% and then back down.  If it's the latter and you are mostly seeing it in Firefox or Thunderbird, that's fairly normal behavior.  I talked to an nvidia developer about it and he said that FF3 creates and frees tons of little pixmaps for no good reason and that's not something that's well optimized in the nvidia driver.  I don't like to defend nvidia but, it really is an application problem and not a driver problem.

---

### Post by Gregstar on 2008-09-10
Hi vor!

Thank you for your answer!

No, it appears about 10 minutes after I start to work on the machine and suddenly the cpu load goes up. XServer uses about 70% of the cpus, but constantly.

But I think I've figured it out -> AllTray isn't working very well -> it forget to put on trayicons or just does'nt show up at all. Now I am working without it and until now, the heavy load is gone. So I hope the best. 

That's one of the negs of small os projects -> if the one and only developer doesn't want anymore, the project stands still or even worse, it's getting shut downed.

But thank you for your information!

---

