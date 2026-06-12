---
title: "need to bring up system settings to fix display"
date: 2020-02-29
forum: Desktop Environments
---

### Post by jgw on 2020-02-29
This machine runs all the time.  When I get up, in the morning, I check things out and my screen in firefox is set to something that is not right.   The screen, without firefox is also wrong.  Then, to make it right, I run settings.  Soon as settings comes up the screen reverts to how its supposed to look.  My signature has my screen settings.  The settings for the display resolution doesn't change at all.  It does this all on its own.  This is pretty mysterious and I can live with it but wonder what is going on.

Thank you.............

---

### Post by Autodave on 2020-02-29
What video card, if any, are you using?  Did you install any driver for it?  If so, what one and where did you get it from?

---

### Post by jgw on 2020-02-29
thank you for the reply......

Processor: AMD® A8-7650k radeon r7, 10 compute cores 4c+6g × 4
Resolution: 3840x2160 pixels

sudo lshw -c video | grep 'configuration'  got me 'radeon'

```
reg@movies:~$ sudo lshw -c video
[sudo] password for greg: 
  *-display                 
       description: VGA compatible controller
       product: Kaveri [Radeon R7 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:39 memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:c0000-dffff

greg@movies:~$ sudo lspci -vnn | grep -i VGA -A 12
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 Graphics] [1002:1313] (prog-if 00 [VGA controller])
	Subsystem: Gigabyte Technology Co., Ltd Kaveri [Radeon R7 Graphics] [1458:d000]
	Flags: bus master, fast devsel, latency 0, IRQ 39
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=8M]
	I/O ports at f000 [size=256]
	Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
--
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64

00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7809] (rev 11) (prog-if 10 [OHCI])
	Subsystem: Gigabyte Technology Co., Ltd FCH USB OHCI Controller [1458:5004]
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at feb6c000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci

00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 0 [1022:141a]
	Flags: fast devsel

00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 1 [1022:141b]

```

I also went to software and updates and checked for additional drivers and none are listed.  Apparently the system has decided on the driver.  Up to know I have always used an additional drive.  I will research this a bit more.  I am currently not on that system but will be in a bit.```

```

---

### Post by jgw on 2020-04-05
bump

---

### Post by jgw on 2020-04-10
I have no idea what happened.  I got an email notification that somebody had replied but I can't find the reply.  I was told that the responder posted:
To change your screen resolution, use the drop-down menu under Display resolution. Note: You should use the Recommended resolution. If you change the resolution, content might appear blurry or pixelated.

First - thank you for the reply.
This is not a resolution problem as it happens in a couple of my machines.  The fix is really simple - just ring settings and it gets fixed automatically.  The bad display, which comes up whenever the system is booted, is always larger than the one that it calls for.  I guess its just another mystery to live with.  No problem...........

---

