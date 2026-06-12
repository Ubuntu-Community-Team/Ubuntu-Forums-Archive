---
title: "screen cut on scroll using chrome"
date: 2017-06-18
forum: Desktop Environments
---

### Post by cryptoz2 on 2017-06-18
I had to take a video and then screenshot the video to show what is happening, sorry it is so blurry but the cut is clear on my screen.  always in the same place and jagged like the screen is broken.  Only happens on mate and with chrome. any ideas what is going on here?  I was only able to upload 2 pics,

---

### Post by RobGoss on 2017-06-18
It looks like a driver issue to me what are the specs for your machine it will help others trouble shoot your problem

What version of Ubuntu are you currently using?

---

### Post by cryptoz2 on 2017-06-18
> **RobGoss said:**
> It looks like a driver issue to me what are the specs for your machine it will help others trouble shoot your problem

What version of Ubuntu are you currently using?

Thanks for the reply.

Using MATE 17.04

[COLOR=#212529][FONT=Inconsolata]lspci -v | less
[/FONT][/COLOR]```


00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1566
        Subsystem: Lenovo Device 36ab
        Flags: bus master, fast devsel, latency 0


00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (prog-if 00 [VGA controller])
        Subsystem: Lenovo Mullins [Radeon R4/R5 Graphics]
        Flags: bus master, fast devsel, latency 0, IRQ 42
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d0000000 (64-bit, prefetchable) [size=8M]
        I/O ports at f000 [size=256]
        Memory at fea00000 (32-bit, non-prefetchable) [size=256K]
        Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: radeon
        Kernel modules: radeon, amdgpu


00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
        Subsystem: Lenovo Kabini HDMI/DP Audio
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at fea64000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel


00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
        DeviceName:  Onboard IGD
        Flags: fast devsel


00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 25
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: d0900000-d0afffff
        Prefetchable memory behind bridge: 00000000d0b00000-00000000d0cfffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp


00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fe900000-fe9fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp


00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: fe800000-fe8fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp


00:02.5 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fe700000-fe7fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp


00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1537
        Subsystem: Advanced Micro Devices, Inc. [AMD] Device 1537
        Flags: bus master, fast devsel, latency 0
        Memory at d0800000 (64-bit, prefetchable) [size=128K]
        Memory at fe600000 (32-bit, non-prefetchable) [size=1M]
        Memory at fea6f000 (32-bit, non-prefetchable) [size=4K]
        Memory at fea6a000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: ccp
        Kernel modules: ccp


00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11) (prog-if 30 [XHCI])
        Subsystem: Lenovo FCH USB XHCI Controller
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fea68000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: xhci_hcd


00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
        Subsystem: Lenovo FCH SATA Controller [AHCI mode]
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 39
        I/O ports at f140 [size=8]
        I/O ports at f130 [size=4]
        I/O ports at f120 [size=8]
        I/O ports at f110 [size=4]
        I/O ports at f100 [size=16]
        Memory at fea6e000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci


00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39) (prog-if 20 [EHCI])
        Subsystem: Lenovo FCH USB EHCI Controller
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        Memory at fea6d000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci


00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39) (prog-if 20 [EHCI])
        Subsystem: Lenovo FCH USB EHCI Controller
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        Memory at fea6c000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci




00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
        Subsystem: Lenovo FCH SMBus Controller
        Flags: 66MHz, medium devsel
        Kernel driver in use: piix4_smbus
        Kernel modules: i2c_piix4, sp5100_tco


00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
        Subsystem: Lenovo FCH Azalia Controller
        Flags: bus master, slow devsel, latency 32, IRQ 16
        Memory at fea60000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel


00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
        Subsystem: Lenovo FCH LPC Bridge
        Flags: bus master, 66MHz, medium devsel, latency 0


00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
        Flags: fast devsel


00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
        Flags: fast devsel


00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
        Flags: fast devsel


00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
        Flags: fast devsel
        Capabilities: <access denied>
        Kernel driver in use: k10temp
        Kernel modules: k10temp


00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
        Flags: fast devsel
        Kernel driver in use: fam15h_power
        Kernel modules: fam15h_power


00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
        Flags: fast devsel




```[COLOR=#212529][FONT=Inconsolata]
[/FONT][/COLOR]lshw -class display

```
  *-display                        description: VGA compatible controller
       product: Mullins [Radeon R4/R5 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:42 memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:fea00000-fea3ffff memory:c0000-dffff



```

---

### Post by cryptoz2 on 2017-06-18
when I try to upload screenshots onto this site I get 502 error #2038

---

### Post by RobGoss on 2017-06-19
You can use the **Go advanced** tab this will allow you to add screen shots, just use the **paper clip**

---

### Post by RobGoss on 2017-06-19
You can also try using the **proprietary drivers** provided by Ubuntu, open Software & Updates, then click on **Additional drivers**. Make sure you are connected to the internet so you ca search for the drivers needed

---

### Post by cryptoz2 on 2017-06-19
> **RobGoss said:**
> You can also try using the **proprietary drivers** provided by Ubuntu, open Software & Updates, then click on **Additional drivers**. Make sure you are connected to the internet so you ca search for the drivers needed

Thanks, there was no driver for the graphics card, one for AMD micro processor but that has not changed anything.

---

### Post by RobGoss on 2017-06-20
Have you tried 16.04.2 to see how it performs? 

The best thing about Linux is you have a lot to choose from

---

### Post by cryptoz2 on 2017-06-20
yep, all other flavors work fine, but mate works best for everything else.  not using mate seems counter productive verses finding the problem and solution.

---

### Post by RobGoss on 2017-06-21
So are you using Mate now and is everything working as it should

---

### Post by cryptoz2 on 2017-06-22
> **RobGoss said:**
> So are you using Mate now and is everything working as it should

 Everything except chrome... and Thunderbird, the same break/cut is seen on webpages in the preview plane.

---

