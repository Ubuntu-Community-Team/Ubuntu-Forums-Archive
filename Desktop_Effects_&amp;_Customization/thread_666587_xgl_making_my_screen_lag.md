---
title: "xgl making my screen lag"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by Himie on 2008-01-13
hi i have a SiS video card, kinda oldish but on windows i dont have the same problem, i install xserve-xgl for enabling desktop effects but when i open a window it loads by triangles and if i try moving the window it looks as if i didnt have installed the video driver, everything becomes more slow and looks weird

is there another gl other than xgl? or how can i stop the screen lag

---

### Post by mrblue182 on 2008-01-13
I have the same problem, and its really annoying not being able to watch videos fullscreen or play games.

---

### Post by Himie on 2008-01-14
bump...

---

### Post by Himie on 2008-01-16
bump again...

---

### Post by Digger78 on 2008-01-16
which chipset?

 I would recommend forgetting about 3D desktop effects. The SiS driver that you have is probably only 2D.

---

### Post by Himie on 2008-01-16
> **Digger78 said:**
> which chipset?

 I would recommend forgetting about 3D desktop effects. The SiS driver that you have is probably only 2D.

but it works fine on windows i can play many 3D games but not those that need really good graphics card like WoW and i can play flyff

---

### Post by Digger78 on 2008-01-16
Thats because the correct drivers are installed in windows.

ubuntu needs the full 3D linux driver.

could you post the output from

```
lspci -v
```

---

### Post by Himie on 2008-01-16
```
himie@himie-desktop:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 01)
        Flags: bus master, medium devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: dfd00000-dfefffff
        Prefetchable memory behind bridge: cfa00000-dfbfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 0c00 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step)
        Flags: bus master, medium devsel, latency 128
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ff00 [size=16]

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
        Subsystem: Silicon Integrated Systems [SiS] AC'97 Modem Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at d400 [size=256]
        I/O ports at d000 [size=128]
        Capabilities: <access denied>

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Unknown device a007:1019
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at dc00 [size=256]
        I/O ports at d800 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 12
        Memory at dfff8000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at dfff9000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at dfffa000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 2.0 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 12
        Memory at dfffb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: Silicon Integrated Systems [SiS] SiS900 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at cc00 [size=256]
        Memory at dfff7000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at dffc0000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at c800 [size=256]
        Memory at dfff6f00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at dffa0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
        Flags: 66MHz, medium devsel, IRQ 5
        BIST result: 00
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Memory at dfee0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 9c00 [size=128]
        Capabilities: <access denied>

himie@himie-desktop:~$ 

```

---

### Post by Digger78 on 2008-01-16
you could have a read through [http://www.winischhofer.eu/linuxsispart1.shtml](http://www.winischhofer.eu/linuxsispart1.shtml)

when it comes to choosing a download i have no idea which one you would need.

alternatively, you could try getting the driver from your motherboard manufacturer (sis claim that all drivers they develope are sent to their customers - mobo manufacturers) and if that fails you could try getting it directly from SiS (their website only has RedHat drivers availabe for download)

I'm currently trying to get the sis 672 driver, and i think i have more chance finding the "san graal"

FSC have claimed that they only have XP and vista drivers

I'm currently waiting to hear back from SiS , i e-mailed the driver developer and he has passed my request to his supervisor. (i won't be holding my breath)

Which ever you choose, I wish you the best of luck.

---

### Post by Himie on 2008-01-17
ok thx let me know if SiS can help with this

---

