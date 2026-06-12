---
title: "Desktop not accelerated?"
date: 2013-03-29
forum: Desktop Environments
---

### Post by sugarat on 2013-03-29
Hi everyone, 

 I have installed Ubuntu on my PC and then the Gnome3 packages, as I really like the Gnome3 interface. 

It doesn't seem as though this environment is accelerated/composited at all.  When I have a number of Windows open and use the expose-style mouse flick to show all open Windows on the screen, it's really quite jerky.  

[LIST]
[*]How do I check that compositing is turned on?
[*]
[/LIST]

Many thanks

---

### Post by The Cog on 2013-03-29
Try using the command
```
lspci -v
```and look for the video controller. Post the output of that.
The last line tells you the kernel driver in use.
As an example, here's mine:
```
01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce GTS 250] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 8303
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at d800 [size=128]
	[virtual] Expansion ROM at febe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	[COLOR="#FF0000"]Kernel driver in use: nvidia[/COLOR]

```

---

### Post by sugarat on 2013-03-29
Hi The Cog, 

 I think its currently running on i915, but the nvidia card in this system is also listing a couple of kernel modules I notice.  I'm positive its running on the intel driver at the moment however. 

```

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
	Subsystem: Dell Device 054b
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f6000000-f70fffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 054b
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
	Subsystem: Dell Device 054b
	Flags: bus master, medium devsel, latency 0, IRQ 41
	Memory at f7c00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Dell Device 054b
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at f7c1a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Dell Device 054b
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f7c18000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Dell Device 054b
	Flags: bus master, fast devsel, latency 0, IRQ 52
	Memory at f7c10000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: f7b00000-f7bfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f7a00000-f7afffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: f7900000-f79fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f7800000-f78fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Dell Device 054b
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f7c17000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation H77 Express Chipset LPC Controller (rev 04)
	Subsystem: Dell Device 054b
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: lpc_ich

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 04)
	Subsystem: Dell Device 054b
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 47
	I/O ports at f0b0 [size=8]
	I/O ports at f0a0 [size=4]
	I/O ports at f090 [size=8]
	I/O ports at f080 [size=4]
	I/O ports at f060 [size=32]
	Memory at f7c16000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
	Subsystem: Dell Device 054b
	Flags: medium devsel, IRQ 11
	Memory at f7c15000 (64-bit, non-prefetchable) [size=256]
	I/O ports at f040 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 640M] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 054b
	Flags: fast devsel, IRQ 16
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at f7000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel modules: nouveau, nvidiafb

02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
	Subsystem: Dell Device 054b
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at f7b01000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: rtsx_pci
	Kernel modules: rts_pstor, rtsx_pci

02:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
	Subsystem: Dell Device 054b
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f7b00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:00.0 USB controller: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller (rev 02) (prog-if 30 [XHCI])
	Subsystem: Dell Device 054b
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f7a00000 (64-bit, non-prefetchable) [size=64K]
	Memory at f7a10000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd

04:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
	Subsystem: Dell Device 0209
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f7900000 (64-bit, non-prefetchable) [size=512K]
	Expansion ROM at f7980000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

05:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)
	Subsystem: Dell Device 054b
	Flags: bus master, fast devsel, latency 0, IRQ 51
	Memory at f7800000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at d000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: alx
	Kernel modules: alx

```

---

### Post by Yellow Pasque on 2013-03-29
Post your /var/log/Xorg.0.log

---

### Post by markbl on 2013-03-29
```

glxinfo | grep render

```
If the output says "direct rendering: no" or you are using software rasterizer then you do not have 3D acceleration.

---

### Post by sugarat on 2013-03-31
```

adam@adam-PC:/sys/class/backlight$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Desktop x86/MMX/SSE2
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 

```

So it looks like Direct rendering is on.  Hmm. Why then does it jerk and look not very smooth when I expose all of my open Windows.. Hmm.

---

