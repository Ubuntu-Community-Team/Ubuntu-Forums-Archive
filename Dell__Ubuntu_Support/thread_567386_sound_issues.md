---
title: "sound issues"
date: 2007-10-04
forum: Dell  Ubuntu Support
---

### Post by moparfan90 on 2007-10-04
i have a new inspiron 1521 and i installed ubuntu 7.10 beta on it. everything but the sound works fine. i cant find anything on the forum that works. i did this command "lspci -v" and got the following (i dont know if this helps)

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fe900000-feafffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: [44] HyperTransport: MSI Mapping
        Capabilities: [b0] Subsystem: Dell Unknown device 01fc

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Memory behind bridge: fe800000-fe8fffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [b0] Subsystem: Dell Unknown device 01fc
        Capabilities: [b8] HyperTransport: MSI Mapping

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fe600000-fe7fffff
        Prefetchable memory behind bridge: 00000000f0100000-00000000f03fffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [b0] Subsystem: Dell Unknown device 01fc
        Capabilities: [b8] HyperTransport: MSI Mapping

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at 6eb0 [size=8]
        I/O ports at 6eb8 [size=4]
        I/O ports at 6ec0 [size=8]
        I/O ports at 6ec8 [size=4]
        I/O ports at 6ee0 [size=16]
        Memory at 88000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [60] Power Management version 2

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at ffb00000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at ffb01000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at ffb02000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at ffb03000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at ffb04000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        Memory at ffa80000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e4] Debug port

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
        Subsystem: Dell Unknown device 01fc
        Flags: 66MHz, medium devsel
        I/O ports at 10c0 [size=16]
        Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at bfa0 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Dell Unknown device 01fc
        Flags: slow devsel, IRQ 16
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
        Memory behind bridge: fe500000-fe5fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, fast devsel, latency 64, IRQ 23
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at ee00 [size=256]
        Memory at fea00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [50] Power Management version 2
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, fast devsel, latency 64, IRQ 22
        Memory at fe5fe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at fe5fd800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at fe5fd400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, medium devsel, latency 64, IRQ 7
        Memory at fe5fd500 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, medium devsel, latency 64, IRQ 7
        Memory at fe5fd600 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Dell Unknown device 01fc
        Flags: bus master, medium devsel, latency 64, IRQ 7
        Memory at fe5fd700 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
        Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
        Memory at f0000000 (64-bit, prefetchable) [size=1M]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0

```


any ideas? anything is helpful. thanks

---

### Post by derby007 on 2007-10-05
OK, did you try the sound option in the menus, I think its on the APPLICATIONS>PREFERENCES>VOLUME_CONTROL or similar, you should get a GUI which lets you pick a MIXER that controls sound levels, ie. muting etc. <Forgive me as I am away from my Ubuntu box at the mo>

Also try : dmesg | grep -i alsa
This tells you that ALSA loaded OK (or not).

Try : aplay -l
Tells you what cards/devices are there.

Check out guide @:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Or @:
[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)

I also see sound problems online @:
[https://bugs.launchpad.net/gstreamer/+bug/131711](https://bugs.launchpad.net/gstreamer/+bug/131711)

---

### Post by moparfan90 on 2007-10-05
thanks for your help. ill try all that and let you know if it works

---

### Post by ~chinook~ on 2007-10-06
I have the same problem. Any help would be appreciated. I have done all of the above steps, no dice.

---

### Post by moparfan90 on 2007-10-07
```
moparfan90@moparfan90-laptop:~$ aplay -l
aplay: device_list:204: no soundcards found...

```
that didnt work



and i cant find my soundcard in the list of devices... any ideas?

it says on the dell site that i have "High Definition Audio 2.0"
i dont know what that means

---

### Post by ~chinook~ on 2007-10-08
> **moparfan90 said:**
> ```
moparfan90@moparfan90-laptop:~$ aplay -l
aplay: device_list:204: no soundcards found...

```
that didnt work



and i cant find my soundcard in the list of devices... any ideas?

it says on the dell site that i have "High Definition Audio 2.0"
i dont know what that means


I found the fix

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Cheers

---

