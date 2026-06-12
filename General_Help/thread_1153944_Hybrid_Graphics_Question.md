---
title: "Hybrid Graphics Question"
date: 2009-05-09
forum: General Help
---

### Post by dtuza on 2009-05-09
Hi, I've recently purchased a Benq Joybook S42 notebook.  This came with hybrid graphics - uses Intel onboard graphics as well as an Nvidia Geforce 9600M GT.  I'm dual booting Ubuntu on this machine and from the performance I've been getting I think Ubuntu is using onboard graphics at all times - I'd really prefer it to use the Nvidia card at all times.  I've read in various other threads that editing xorg.conf would be required to make this happen - is this the only way?  If so, I could very much use some help on the logistics of how exactly to edit the config file - if not, would be very interested to hear alternatives.  Any help is much appreciated, thanks.

```
$ lspci -v

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Benq Corporation Device 0597
	Flags: bus master, fast devsel, latency 0, IRQ 2294
	Memory at f3000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

.
.
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
	Subsystem: Benq Corporation Device 0597
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

```

```
$ cat /etc/X11/xorg.conf
.
.

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2960 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

---

