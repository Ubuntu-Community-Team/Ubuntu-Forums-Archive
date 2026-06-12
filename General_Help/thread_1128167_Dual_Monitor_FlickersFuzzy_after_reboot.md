---
title: "Dual Monitor Flickers/Fuzzy after reboot"
date: 2009-04-17
forum: General Help
---

### Post by buddywilliams on 2009-04-17
Every time I turn on my laptop (Dell, docking station with two monitors external monitors), my right monitor flickers until I adjust refresh rate with the Monitor Resolution Settings tool. It doesn't matter which refresh rate I set it to just that I change it. When I click Apply the monitor turns off then back on and looks like it should.

Here's my xorg.conf:
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2560 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

---

### Post by nilsm on 2009-11-12
I have the same problem with Ubuntu 9.10. Using ATI binary drivers and the same resolution.
Did you ever find out the cause?

---

