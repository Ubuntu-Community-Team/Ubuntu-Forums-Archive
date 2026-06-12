---
title: "Cannot select or force native resolution"
date: 2009-10-01
forum: Desktop Environments
---

### Post by sjprice on 2009-10-01
So have had issues the last 3 days. After a reboot, all of a sudden my resolution dropped from native 1680x1050 to 1024x768. I had been logging off for weeks, but the reboot killed it for some reason.

I wont go through all my steps, but I have checked xorg.conf and tried to force the resolution. I have reinstalled Nvidia driver from Nvidia, and from repos. I reformatted the / partition (needed it anyway), but still nothing. I now have the following log (only Warnings)and .conf

```
(WW) NVIDIA(GPU-0): The EDID read for display device CRT-1 is invalid: the
(WW) NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(**) NVIDIA(0): Virtual screen size configured to be 1680 x 1050
(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-1's EDID.
```

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	1680 1050
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	#	Driver		"nvidia"
EndSection
```

Using the Nvidia X Server settings, I can only select up to 1360x768.

I think the reason EDID is not working is I have the box on a KVM.

Any ideas or new steps in resolving this mess?

Thanks!

---

### Post by sjprice on 2009-10-01
Solved. Bad monitor cable. Wish I would have tried that 2 days ago...

---

