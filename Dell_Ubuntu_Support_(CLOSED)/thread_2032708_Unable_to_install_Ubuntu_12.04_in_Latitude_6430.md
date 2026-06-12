---
title: "Unable to install Ubuntu 12.04 in Latitude 6430"
date: 2012-07-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Muixca on 2012-07-24
Greetings!
I am trying to install 12.04 on a Latitude 6430 to no avail. Been a week  on this. DELL has never given me issues since 7.04 but this time, big time! I am currently running 10.10 which is the only version with which I could get screen and (wired) connection; no wireless-yet-, no card reader, no audio... but yes a system that starts. I managed to install the NVIDIA graphic drivers but not the audio.

Both with 32 and 64 versions I can get to the installation screen hitting F6, from there I have tried to install every single option (nomodeset and the like) but it always ends up with a cursor blinking in the left upper corner. Interestingly the alternate install, installs but stalls upon restart. It gives me a scrambled startup screen. No login possible.
I suspect it is a ^bug^ in the installer with the graphic environment.

Any advice, instructions HIGHLY appreciated.
m~

 Output of lspci -v, -aplay -l, lshw -l (as attachement) herewith.

*aplay
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

*lspci
00:00.0 Host bridge: Intel Corporation Device 0154 (rev 09)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Device 0151 (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f5000000-f60fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:14.0 USB Controller: Intel Corporation Device 1e31 (rev 04) (prog-if 30)
    Subsystem: Dell Device 0534
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7720000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd

00:16.0 Communication controller: Intel Corporation Device 1e3a (rev 04)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f773c000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f7700000 (32-bit, non-prefetchable) [size=128K]
    Memory at f7739000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation Device 1e2d (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0534
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7738000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Device 1e20 (rev 04)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 4
    Memory at f7730000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation Device 1e10 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Device 1e12 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f7600000-f76fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation Device 1e14 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=07, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f6b00000-f74fffff
    Prefetchable memory behind bridge: 00000000f2b00000-00000000f34fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation Device 1e16 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=0b, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f6100000-f6afffff
    Prefetchable memory behind bridge: 00000000f2100000-00000000f2afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation Device 1e1a (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
    Memory behind bridge: f7500000-f75fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation Device 1e26 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0534
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at f7737000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Device 1e55 (rev 04)
    Subsystem: Dell Device 0534
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 04)
    Subsystem: Dell Device 0534
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 48
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f020 [size=32]
    Memory at f7736000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation Device 1e22 (rev 04)
    Subsystem: Dell Device 0534
    Flags: medium devsel, IRQ 11
    Memory at f7735000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Device 0dfc (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at f6000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f6080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

03:00.0 Network controller: Intel Corporation 6000 Series Gen2 (rev 34)
    Subsystem: Intel Corporation Device 1321
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f7600000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>

0c:00.0 SD Host controller: O2 Micro, Inc. Device 8221 (rev 05) (prog-if 01)
    Subsystem: Dell Device 0534
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7502000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

---

### Post by scogut on 2012-10-28
I just purchased a Latitude E6430s pre-installed from Dell with 11.04 x64.  It came with the Dell drivers.  I am not sure if this can help you since it is a different version of your model.  I am new to linux but willing to help if you are still searching.

---

