---
title: "yet another no sound problem"
date: 2009-06-19
forum: General Help
---

### Post by chaoszerox on 2009-06-19
It seems that a lot of people have no sound problems =/ I seem to be one of them

Heres some info
Ubuntu 9.04

> chaos@chaoszerox:~$ aplay -l
aplay: device_list:217: no soundcards found...> [B]chaos@chaoszerox:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
    Subsystem: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge
    Flags: bus master, fast devsel, latency 0
    Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
    Flags: bus master, 66MHz, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    Memory behind bridge: fc900000-fe9fffff
    Prefetchable memory behind bridge: e4500000-f46fffff
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
    Subsystem: Dell Device 0132
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at e800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
    Subsystem: Dell Device 0132
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at e880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
    Subsystem: Dell Device 0132
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ec00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
    Subsystem: Dell Device 0132
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: f4700000-f47fffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 0132
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Memory at 30000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
    Subsystem: Dell Device 0132
    Flags: medium devsel, IRQ 3
    I/O ports at e480 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)
    Subsystem: nVidia Corporation Device 0132
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at f4680000 (32-bit, prefetchable) [size=512K]
    [virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb, rivafb

02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: GVC Corporation Device 0001
    Flags: bus master, medium devsel, latency 64, IRQ 22
    I/O ports at d800 [size=256]
    Memory at feaffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

chaos@chaoszerox:~$ [/B]

---

### Post by Quarkrad on 2009-06-19
I too had this problem and googled for ages - try this, it worked for me.  open up the terminal and enter the command:
alsamixer

A window should pop up showing various volume controls you can increase/decrease.  Use the left/right arrow keys to move to another vol control and the up/down arrow keys to adjust.   It might work for your setup.

---

### Post by chaoszerox on 2009-06-19
> **Quarkrad said:**
> I too had this problem and googled for ages - try this, it worked for me.  open up the terminal and enter the command:
alsamixer

A window should pop up showing various volume controls you can increase/decrease.  Use the left/right arrow keys to move to another vol control and the up/down arrow keys to adjust.   It might work for your setup.


> [B]chaos@chaoszerox:~$ aplay -l
aplay: device_list:217: no soundcards found...
[/B]

**sound volume isn't the issue, but thanks for the reply =)**

---

### Post by m4tic on 2009-06-19
reinstall the system

---

### Post by dmizer on 2009-06-19
> **m4tic said:**
> reinstall the system

This is not going to solve a problem with soundcard detection.

Please see this thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

And this thread: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by chaoszerox on 2009-06-19
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Thats the thread I started with (see first post). I seem to need the driver or something related to the driver.

A little info on my system:
no onboard GFX, sound, or ethernet. It's all on the IDE and AGP (GFX)
I'm pretty sure the soundcard is a "sound blaster"
Dell Demension 4500s
P4 2.53 GHz
512 DDR 266 MHz
NVIDIA GeForce Ti 4200


if I only knew what/where to search...The link in step 3 seems to be broken ```
http://www.alsa-project.org/alsa-doc/
```

---

### Post by chaoszerox on 2009-06-19
shameless self-bump

---

### Post by dmizer on 2009-06-19
I would say you have a completely unsupported sound card. Are you sure it's enabled in the BIOS?

---

### Post by chaoszerox on 2009-06-19
> **dmizer said:**
> I would say you have a completely unsupported sound card. Are you sure it's enabled in the BIOS?
I just checked the BIOS and yes it should be... The front panel seems to plug into my sound card as well....so my soundcard can't be entirely dead

---

### Post by Yellow Pasque on 2009-06-19
> I would say you have a completely unsupported sound card.
It should still show up in lspci if the BIOS recognizes it, regardless of whether a valid kernel module/driver is available.

Try the card in a different PCI slot.

---

### Post by chaoszerox on 2009-06-22
> **Temüjin said:**
> Try the card in a different PCI slot.
Well I reinstalled windows, and the sound was working with that a week ago, so I figured if if it wasn't a software problem it was hardware. I read ur post after I did what u advised me to do lol

---

