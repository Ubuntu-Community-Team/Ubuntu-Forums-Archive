---
title: "X resolution and strange display, intel, maverick"
date: 2011-05-07
forum: Desktop Environments
---

### Post by shmeeter on 2011-05-07
Hi.  Thanks in advance.

I'm trying to get a higher resolution in X.  Currently anything but 1024x768 displays a partial, shifted screen.  (See screenshot.  Notice that the mouse cursor is in the black area.  This screenshot was originally 1600x1200.  I have tried adjusting my monitor.)

My xorg.conf:
```

Section "Monitor"
	Identifier "monitor0"
	VendorName "Compaq"
	ModelName "V1000"
	HorizSync 30-107
	VertRefresh 48-160
#	Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
#	Modeline "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
EndSection

Section "Device"
	Identifier "device0"
	Driver "intel"
EndSection

Section "Screen"
	Identifier "screen0"
	Device "device0"
	Monitor "monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"layout0"
	Screen		0	"screen0"
EndSection

```
Notice I have tried some Modeline stuff.  The Modes "1280x1024" part does not work.
Here is my cvt output:
```

# 1600x1200 59.87 Hz (CVT 1.92M3) hsync: 74.54 kHz; pclk: 161.00 MHz
Modeline "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync

```  
I'm thinking intel driver problems?  You need anything else?  lspci -v?
```

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company D530 sff(dc578av)
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at fc400000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 14d0 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [d0] Power Management version 1
	Kernel driver in use: i915
	Kernel modules: i915

```
I seem to remember this all working with earlier versions, live CDs, etc, so...  Shouldn't be too tough?

Thanks again.

---

