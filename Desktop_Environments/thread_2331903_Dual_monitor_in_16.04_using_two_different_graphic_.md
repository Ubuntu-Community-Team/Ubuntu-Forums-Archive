---
title: "Dual monitor in 16.04 using two different graphic cards"
date: 2016-07-26
forum: Desktop Environments
---

### Post by limit2 on 2016-07-26
I have two cards GTX 630 and GTX 610. I've installed nvidia 365 drivers. If I run nvidia settings and then enable the second display then restart lightdm, I see only a blank screen on the secondary monitor, I can move the mouse over there though. If I enable [FONT=Ubuntu][COLOR=#111111]Xinerama and restart lightdm, I can see the background image on the secondary monitor, a ubuntu logo is centered as well and I can't move mouse. When I open system settings -> and click on Display, it says Xrandr extention is not present. xrandr command says extension is not enabled or something like that. Do note: xrandr issue happens only if I enable Xinerama, otherwise that command works fine and lists info.

[/COLOR][/FONT]To summarize, without Xinerama blank screen will be displayed, with Xinerama background will be displayed. I don't see any taskbar on the right window. I've even tried enabling Base Mosiac instead of Xinerama and it disables the second montior after lightdm restart. 

Should I be installing some other package for this to work? 


xorg.conf

[http://pastebin.com/2PmB07Jh](http://pastebin.com/2PmB07Jh)

lspci -v

```
01:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 630 Rev. 2] (rev a1) (prog-if 00 [VGA controller])Subsystem: ZOTAC International (MCO) Ltd. GK208 [GeForce GT 630 Rev. 2]
Flags: bus master, fast devsel, latency 0, IRQ 30
Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
Memory at e0000000 (64-bit, prefetchable) [size=128M]
Memory at e8000000 (64-bit, prefetchable) [size=32M]
I/O ports at e000 [size=128]
[virtual] Expansion ROM at f7000000 [disabled] [size=512K]
Capabilities: <access denied>
Kernel driver in use: nvidia
Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
Subsystem: ZOTAC International (MCO) Ltd. GK208 HDMI/DP Audio Controller
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel
Kernel modules: snd_hda_intel

02:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 610] (rev a1) (prog-if 00 [VGA controller])
Subsystem: ASUSTeK Computer Inc. GF119 [GeForce GT 610]
Flags: bus master, fast devsel, latency 0, IRQ 31
Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
Memory at d0000000 (64-bit, prefetchable) [size=128M]
Memory at d8000000 (64-bit, prefetchable) [size=32M]
I/O ports at d000 [size=128]
[virtual] Expansion ROM at f5000000 [disabled] [size=512K]
Capabilities: <access denied>
Kernel driver in use: nvidia
Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

02:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
Subsystem: ASUSTeK Computer Inc. GF119 HDMI Audio Controller
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at f5080000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel

```

lshw -c video
[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]```
*-display               
   description: VGA compatible controller
   product: GK208 [GeForce GT 630 Rev. 2]
   vendor: NVIDIA Corporation
   physical id: 0
   bus info: pci@0000:01:00.0
   version: a1
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
   configuration: driver=nvidia latency=0
   resources: irq:30 memory:f6000000-f6ffffff memory:e0000000-e7ffffff memory:e8000000-e9ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display
   description: Display controller
   product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
   vendor: Intel Corporation
   physical id: 2
   bus info: pci@0000:00:02.0
   version: 09
   width: 64 bits
   clock: 33MHz
   capabilities: msi pm bus_master cap_list
   configuration: driver=i915 latency=0
   resources: irq:27 memory:f7400000-f77fffff memory:c0000000-cfffffff ioport:f000(size=64)
   *-display
   description: VGA compatible controller
   product: GF119 [GeForce GT 610]
   vendor: NVIDIA Corporation
   physical id: 0
   bus info: pci@0000:02:00.0
   version: a1
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
   configuration: driver=nvidia latency=0
   resources: irq:31 memory:f4000000-f4ffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff [FONT=Consolas][COLOR=#111111]ioport:d000(size=128) memory:f5000000-f507ffff

[/COLOR][/FONT]
```

---

