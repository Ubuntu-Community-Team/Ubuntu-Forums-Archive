---
title: "Hauppauge WinTV-HVR2250 on Ubuntu Desktop"
date: 2011-02-26
forum: Desktop Environments
---

### Post by cnickl on 2011-02-26
Hi everybody,

I'm new to Ubuntu so please be gentle.

I used to run Win7 and watched TV using WMC with my WinTV-HVR2250 and it worked perfect.  The installation of it under Ubuntu is a nightmare so far. Here is what I did:

First I wanted to know if the card is recognized:
```
lspci -v
02:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
	Subsystem: Hauppauge computer works Inc. Device 8891
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fe000000 (64-bit, non-prefetchable) [size=4M]
	Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>
	Kernel driver in use: saa7164
	Kernel modules: saa7164
```
so I guess it is

Then I downloaded the firmware
```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw
```
and copied it into the /lib/firmware folder


The card is not working:
```
dmesg | grep saa
[   17.421662] saa7164 driver loaded
[   17.421702] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.422906] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   17.422912] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfe000000
[   17.422918] saa7164 0000:02:00.0: setting latency timer to 64
[   17.580062] saa7164_downloadfirmware() no first image
[   17.580098] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   17.693141] saa7164_downloadfirmware() Upload failed. (file not found?)
```

I even went to all the recompiling described here:

[http://ubuntuforums.org/archive/index.php/t-1567490.html](http://ubuntuforums.org/archive/index.php/t-1567490.html)

I abandoned it after hours of compiling and still getting errors.

then I noticed that the firmware I got from the website is
```
v4l-saa7164-1.0.3-3.fw
```
and the boot sequence is looking for
```
v4l-saa7164-1.0.3.fw
```

Am I missing something? I tried
```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3.fw
```
but that resulted in a website not found

How do I get the correct firmware? Any help is appreciated

Chris

---

