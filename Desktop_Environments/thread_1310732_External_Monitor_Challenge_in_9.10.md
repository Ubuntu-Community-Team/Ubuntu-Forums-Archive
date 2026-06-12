---
title: "External Monitor Challenge in 9.10"
date: 2009-11-02
forum: Desktop Environments
---

### Post by joebrueske on 2009-11-02
For the longest time I've been using an external monitor since my laptop's LCD screen is going. When I switched over to 9.10 I can't get the display to stabilize when I turn off the laptop's display. It simply wigs out and looks as if the refresh rate is wrong. Yet, even when I change the refresh rate or resolution it stays the same or the monitor turns off because the "Frequency [is] out of range."

When I have an extended desktop, it works just fine, but it's a little annoying cause the Panels will be on "Screen 2" instead of "Screen 1" and things are all over the place. 

If I check "Mirrored Desktop" I get the desired effect but I don't want my laptop's screen on. I'd like to get as much life from the LCD as I possibly can. If anyone has any ideas as to what configuration I should have, let me know.

In the meantime, I'll just tape down the screen trigger to keep the screen off. :P If you can't fix the software, hack the hardware!!

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2512 864
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection
```

---

