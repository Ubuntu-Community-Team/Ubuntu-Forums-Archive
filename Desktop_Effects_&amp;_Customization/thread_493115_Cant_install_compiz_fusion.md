---
title: "Cant install compiz fusion"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by sa_ill on 2007-07-05
CAnt install compiz fusion.
tried everything in the popular guides

this is the error that I get

E: /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070705~3v1ubuntu0_i386.deb: trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
 
and i get this when I type  sudo apt-get install -f in the terminal

dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070705~3v1ubuntu0_i386.deb (--unpack):

 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins

Errors were encountered while processing:

 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070705~3v1ubuntu0_i386.deb

E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dannyboy79 on 2007-07-05
you apparently didn't remove desktop-effects, compiz and compiz-core first then. also make sure you disabled Gnome Desktop Effects within System, Prefs, ....

You follow the guide ([http://ubuntuforums.org/showthread.php?t=493074](http://ubuntuforums.org/showthread.php?t=493074))  correctly, and it will work.

---

### Post by sa_ill on 2007-07-05
I did try to open desktop effects but it doesnt open
this is the message that I get

The Composite extension is not available

---

### Post by dannyboy79 on 2007-07-05
ok, well you have to make up your mind. Either go with Desktop Effects built into Fiesty or go with the brand new Beryl/Compiz combination software called Compiz-Fusion. 

If you want compiz to work with your machine, you have to have a graphics card that supports it. Please post the output of this command:

lspci -v

depending on what card, follow the steps here: [http://www.compiz.org/Documentation/Documentation](http://www.compiz.org/Documentation/Documentation)

---

### Post by sa_ill on 2007-07-05
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 82 [Master PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8410 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, slow devsel, latency 64, IRQ 18
        Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=06, subordinate=08, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: c0200000-c02fffff
        Prefetchable memory behind bridge: 50000000-53ffffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 22
        Memory at c8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <access denied>

06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at a000 [size=256]
        Memory at c0210000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0418
        Flags: bus master, medium devsel, latency 168, IRQ 20
        Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at c0211000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=07, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c0210400 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at c0210800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c0210c00 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Flags: medium devsel, IRQ 255
        Memory at c0210100 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: <access denied>

---

### Post by dannyboy79 on 2007-07-05
Ok, well see where it states: 
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M] (prog-if 00 [VGA])
Well, that tells us you have an ATI graphics card. So you need to follow the instructions at compiz.org. I have linked to it here:
[http://www.compiz.org/ATI](http://www.compiz.org/ATI)

If you can't figure it out after giving it a valent attempt, I'll attempt to help you but as I said, I don't use ATI so you may want to scrub the forums here to look for ATI and compiz. There's plenty of people that have done it. Good luck

---

### Post by sa_ill on 2007-07-05
but this is just for compiz

i want to install compiz fusion

---

### Post by dannyboy79 on 2007-07-05
> **sa_ill said:**
> but this is just for compiz

i want to install compiz fusion
First of all, what I linked you to is for setting up your graphics card so that you have accelerated graphics so that you can do compiz, beryl, 3d gaming and the like. I didn't link you to how to install compiz did I? If you want my help, please just do what I am suggesting, I know what you want, you've already posted what your goal is.

---

### Post by dannyboy79 on 2007-07-05
then, either follow this guide: [http://forum.compiz.org/viewtopic.php?t=1325&highlight=compizfusion](http://forum.compiz.org/viewtopic.php?t=1325&highlight=compizfusion)

or the guide I posted in post number 2 of this thread, post #2 uses a version of compiz, compiz-fusion, etc etc that are backported from Gutsy, and he says they are more stable than Trevino's repo.

---

### Post by sa_ill on 2007-07-05
OK ill try it out

---

