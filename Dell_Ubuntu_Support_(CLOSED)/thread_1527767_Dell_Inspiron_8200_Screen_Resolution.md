---
title: "Dell Inspiron 8200 Screen Resolution"
date: 2010-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jim_deadlock on 2010-07-09
I have a Dell Inspiron 8200 running 10.04 (lucid) and as far as I know I'm running the default video driver.

The display is fine and I can view streaming video nicely so I have no major complaints. However, my screen resolution is set at 1600x1200 which is quite small, but when I try to change it to anything else the screen displays a blurry mess. Do I need to do something about my display driver?

---

### Post by ov3rcl0ck on 2010-07-09
You're probably running in framebuffer mode, which will hog RAM, give bad resolution, and take CPU resources rather than GPU.

Tell me what this outputs and I'll gladly walk you through installing the drivers:
```

lspci -v | less

```

Also do you want/need 3D, because 2D drivers will most likely be opensource, they will already be in the repos making it easier to install. But then you won't be able to run 3D games and 3D programs. However I'm experienced with trouble shooting both ATI and NVIDIA, and I can help you with Intel also, but its a bit harder.

---

### Post by jim_deadlock on 2010-07-09
Output is below, I don't need 3D, normal installation will be fine, thanks!

```
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
    Flags: bus master, fast devsel, latency 0
    Memory at e8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
    Flags: bus master, 66MHz, fast devsel, latency 32
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fc000000-fdffffff
    Prefetchable memory behind bridge: e0000000-e7ffffff
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
    Subsystem: Intel Corporation Device 4541
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at bf80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
    Subsystem: Intel Corporation Device 4541
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at bf20 [size=32]
    Kernel driver in use: uhci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=10, sec-latency=32
    I/O behind bridge: 0000e000-0000ffff
    Memory behind bridge: f4000000-fbffffff
    Prefetchable memory behind bridge: 20000000-29ffffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Intel Corporation Device 4541
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at bfa0 [size=16]
    Memory at 2a000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
    Subsystem: Cirrus Logic Device 5959
    Flags: bus master, medium devsel, latency 0, IRQ 5
    I/O ports at d800 [size=256]
    I/O ports at dc80 [size=64]
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
    Subsystem: Conexant Systems, Inc. Device 5421
    Flags: medium devsel, IRQ 5
    I/O ports at d400 [size=256]
    I/O ports at dc00 [size=128]
    Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
    Subsystem: Dell Device 00d4
    Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at c000 [size=256]
    Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at fc000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon

02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
    Subsystem: Dell Device 00d4
    Flags: bus master, medium devsel, latency 32, IRQ 11
    I/O ports at ec80 [size=128]
    Memory at f8fffc00 (32-bit, non-prefetchable) [size=128]
    Expansion ROM at 28000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: 3c59x
    Kernel modules: 3c59x

02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
    Subsystem: Dell Device 00d4
    Flags: bus master, medium devsel, latency 168, IRQ 11
    Memory at f8000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: f4000000-f7fff000
    I/O window 0: 0000e000-0000e0ff
    I/O window 1: 0000e400-0000e4ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
    Subsystem: Dell Device 00d4
    Flags: bus master, medium devsel, latency 168, IRQ 11
    Memory at f8001000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
    Memory window 0: 24000000-27fff000 (prefetchable)
    Memory window 1: 2c000000-2ffff000
    I/O window 0: 0000e800-0000e8ff
    I/O window 1: 0000f000-0000f0ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller (prog-if 10)
    Subsystem: Dell Device 00d4
    Flags: bus master, medium devsel, latency 32, IRQ 11
    Memory at f8fff000 (32-bit, non-prefetchable) [size=2K]
    Memory at f8ff8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

07:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    Subsystem: Linksys Device 4320
    Flags: bus master, fast devsel, latency 64, IRQ 11
    Memory at 2c000000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

```

---

### Post by jim_deadlock on 2010-07-12
I've diligently followed the guide on this page:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

... including the **"KMS with a Radeon card"** section (although it defaults to KMS anyway if this step is not followed).

```
$ dmesg | grep drm
[    0.000000] Linux version 2.6.32-23-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 (Ubuntu 2.6.32-23.37-generic 2.6.32.15+drm33.5)
[   64.566099] [drm] Initialized drm 1.1.0 20060810s
[   65.034056] [drm] radeon kernel modesetting enabled.
[   65.052740] [drm] radeon: Initializing kernel modesetting.
[   65.053061] [drm] register mmio base: 0xFCFF0000
[   65.053065] [drm] register mmio size: 65536
[   65.053403] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   65.053518] [drm] radeon: VRAM 64M
[   65.053521] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
[   65.053524] [drm] radeon: GTT 64M
[   65.053527] [drm] radeon: GTT from 0xE8000000 to 0xEBFFFFFF
[   65.053562] [drm] radeon: irq initialized.
[   65.053712] [drm] Detected VRAM RAM=64M, BAR=128M
[   65.053718] [drm] RAM width 128bits DDR
[   65.054372] [drm] radeon: 64M of VRAM memory ready
[   65.054377] [drm] radeon: 64M of GTT memory ready.
[   65.054630] [drm] radeon: cp idle (0x02000603)
[   65.054806] [drm] Loading R200 Microcode
[   65.162445] [drm] radeon: ring at 0x00000000E8000000
[   65.162471] [drm] ring test succeeded in 1 usecs
[   65.174673] [drm] radeon: ib pool ready.
[   65.174810] [drm] ib test succeeded in 0 usecs
[   65.176749] [drm] Panel ID String: SHP                     
[   65.176756] [drm] Panel Size 1600x1200
[   65.177135] [drm] Default TV standard: NTSC
[   65.177141] [drm] 27.000000000 MHz TV ref clk
[   65.177146] [drm] Default TV standard: NTSC
[   65.177149] [drm] 27.000000000 MHz TV ref clk
[   65.177370] [drm] Radeon Display Connectors
[   65.177374] [drm] Connector 0:
[   65.177377] [drm]   VGA
[   65.177382] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   65.177385] [drm]   Encoders:
[   65.177388] [drm]     CRT1: INTERNAL_DAC1
[   65.177391] [drm] Connector 1:
[   65.177394] [drm]   LVDS
[   65.177396] [drm]   Encoders:
[   65.177399] [drm]     LCD1: INTERNAL_LVDS
[   65.177401] [drm] Connector 2:
[   65.177404] [drm]   S-video
[   65.177406] [drm]   Encoders:
[   65.177409] [drm]     TV1: INTERNAL_DAC2
[   65.303951] [drm] fb mappable at 0xE0040000
[   65.303957] [drm] vram apper at 0xE0000000
[   65.303960] [drm] size 7680000
[   65.303963] [drm] fb depth is 24
[   65.303966] [drm]    pitch is 6400
[   65.313462] fb0: radeondrmfb frame buffer device
[   65.313481] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
```This makes no difference. I still get a blurred mess with any other resolution except 1600x1200 (maximum).

So next I tried creating a file at /etc/X11/xorg.conf like this:

```
Section "Device"
        Identifier      "Radeon RV250"
        Driver          "ati"
        BusID           "PCI:1:0:0"
#        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
#        Option          "DPMS"
#        HorizSync       28-72
#        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon RV250"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
#        InputDevice     "Generic Keyboard"
#        InputDevice     "Configured Mouse"
EndSection
```After rebooting it tried to load in 1024x768 for a couple of seconds but as usual failed, then snapped to 1600x1200

When I boot into windows it can handle various resolutions without any problem so I don't think it's a hardware issue.

Still stumped...

---

### Post by efflandt on 2010-07-15
I temporarily had an Inspiron 8200, but it had different nVidia video and slightly less resolution (although things were small initially).  So I had to do different things to get the proprietary nvidea(96) driver working.

But you do not need to change your resolution to make things bigger.  Start by going to System > Preferences > Appearance and under **Fonts** tab, set larger fonts, and or under the **Details** button there you can set Resolution to more dots per inch to make things larger.  That should make things easier to read.

---

### Post by jim_deadlock on 2010-07-15
Thanks, I already did that and it does help to an extent but I still have to squint at things like Pogo games (Java applets).

---

