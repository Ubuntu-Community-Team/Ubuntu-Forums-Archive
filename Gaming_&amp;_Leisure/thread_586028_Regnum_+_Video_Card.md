---
title: "Regnum + Video Card"
date: 2007-10-21
forum: Gaming &amp; Leisure
---

### Post by AnLGP on 2007-10-21
Hey,

I found out how to get the login screen for regnum working in linux (a lot of folks seem to have a problem with this and this worked for me (while in your Regnum folder):

```
G_SLICE=always-malloc ./rolauncher
```

but it tells me these:

Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version

-

So I checked what kind of file I am using and as I don't know what any of this means to me I'm going to post the output.

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at 52200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 20e0 [size=8]
        Memory at 40000000 (32-bit, prefetchable) [size=256M]
        Memory at 52280000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Gateway 2000 Unknown device 5049
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 522c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: 52300000-523fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: 52400000-524fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 2080 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 2060 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 2040 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 2020 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at 522c4000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 52000000-521fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000051ffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 20b0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 20c8 [size=8]
        I/O ports at 20ec [size=4]
        I/O ports at 20c0 [size=8]
        I/O ports at 20e8 [size=4]
        I/O ports at 20a0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: medium devsel, IRQ 11
        I/O ports at 2000 [size=32]

03:00.0 Multimedia controller: ATI Technologies Inc Theater 550 PRO PCI [ATI TV Wonder 550]
        Subsystem: ATI Technologies Inc Unknown device a346
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at 52000000 (32-bit, non-prefetchable) [size=1M]
        Memory at 50000000 (32-bit, prefetchable) [size=32M]
        Capabilities: <access denied>

03:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
        Subsystem: Conexant Unknown device 2000
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at 52100000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at 1040 [size=8]
        Capabilities: <access denied>

03:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 5050
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at 52115000 (32-bit, non-prefetchable) [size=2K]
        Memory at 52110000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
        Subsystem: Gateway 2000 Unknown device 5049
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at 52114000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1000 [size=64]
        Capabilities: <access denied>

--

what I want to know is -

Is it upgradeable a la option 2 or 3 above:

(2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version)

or is it the first option?

1. Your video card is too old

Thanks.

EDIT:

I have a Gateway GT5018E that was bought (guesstimate) within the last 12-18 months - could it be that my video card is too old?

---

