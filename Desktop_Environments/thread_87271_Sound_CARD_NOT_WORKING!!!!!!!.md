---
title: "Sound CARD NOT WORKING!!!!!!!"
date: 2005-11-07
forum: Desktop Environments
---

### Post by new2linux on 2005-11-07
I recently upgraded to Breezy and have been overwhelmingly happy with it except for the fact that my sound card doesn't appear to be working.  I had both hoary and warty installed previously and had no problems.  

System Specs = 

pIII 500mhz
256mb. ram
dell optiplex GX1

The sound card is integrated.

PLEASE HELP!!!!!!

---

### Post by az on 2005-11-07
Open a terminal and type
lsmod

and

lspci -v

and post the output.


*EDIT* actually, just look in the hardware devices thing and post what it says about your sound card.  If you cannot find anything, post the above.

---

### Post by new2linux on 2005-11-07
There doesn't appear to be a sound card listed in the device manager/list thing.

The output from lspci -v is
> 0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 1.0

0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fc000000-feffffff
        Prefetchable memory behind bridge: f9000000-f9ffffff

0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        I/O ports at ffa0 [size=16]

0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at dce0 [size=32]

0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
        Subsystem: Dell 3C905B Fast Etherlink XL 10/100
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at dc00 [size=128]
        Memory at ff000000 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at fb000000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 1

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: Dell Optiplex GX1 Onboard Display Adapter
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 9
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at ec00 [size=256]
        Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] AGP version 1.0
Thanks!!

---

### Post by az on 2005-11-07
440BX?  It must be on the isa bus, then...

Look here:
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

---

### Post by new2linux on 2005-11-09
Thanks for the Help!

Sound is now working!!!

Thanks Again

---

