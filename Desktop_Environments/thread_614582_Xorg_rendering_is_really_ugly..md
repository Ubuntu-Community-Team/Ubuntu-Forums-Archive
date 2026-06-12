---
title: "Xorg rendering is really ugly."
date: 2007-11-16
forum: Desktop Environments
---

### Post by zhaozhou on 2007-11-16
Hi there.

I've fiddled around in the kernel a bit now, to test things out.
Now, the X rendering is really ugly. I don't really _know_ it has anything to do with my kernel configuration, it might be the fglrx-driver disliking my 2.6.23 kernel, or anything else.

In the attachment you can see how it looks.
It happens when something updates. If i have a window selected, and a window behind it updates, it will bring it to the front, the windowmanager looses it (the windowmanager itself is not brought to the front, just the object inside it).

This is my lspci:
```

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)


```

Anyone have any ideas?

---

### Post by K.Mandla on 2007-11-16
> **zhaozhou said:**
> I don't really _know_ it has anything to do with my kernel configuration, it might be the fglrx-driver disliking my 2.6.23 kernel, or anything else.
That would be my first suspect. If you've managed to trigger some sort of unhappiness between the two, video artifacts might be the result. 

Have you tried a different driver? even the vesa driver, for troubleshooting purposes?

---

### Post by zhaozhou on 2007-11-16
I managed to get the vga driver started, same thing there.
Strange enough, i saw that i still had my old kernel lying around in /boot, so i booted it, and the results are the same.

I haven't tried the vga driver in the old kernel though, but fglrx worked before, it should now.

So, its not a kernel problem after all, and not a driverproblem.

Anyone have any suggestions?
Anything will do, really. Even a clean install, if you think it'll work.

---

### Post by zhaozhou on 2007-11-17
Although i hate bumps, ill do one anyway.

Got any ideas?

---

