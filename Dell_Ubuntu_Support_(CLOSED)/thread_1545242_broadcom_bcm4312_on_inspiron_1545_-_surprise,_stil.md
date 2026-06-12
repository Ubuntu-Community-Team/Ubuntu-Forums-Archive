---
title: "broadcom bcm4312 on inspiron 1545 - surprise, still no wireless!!"
date: 2010-08-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pebeo on 2010-08-03
Hi
I've just installed Lucid on my housemates laptop after singing the praises of ubuntu and the wireless won't connect. been digging around in forums for days and found that the problem is the BCM4312. I've tried everything to fix this but it still says wireless is disabled. Broadcom STA proprietary wireless driver is activated and currently in use, BCMWL-kernel-source & BCMWL-modaliases are installed and I removed the B43-fwcutter

This is the info i get up when i put lapci -v

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
    Subsystem: Dell Device 02aa
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f68fc000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at de00 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Dell Device 000c
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb

It connects fine with the ethernet cable but if i don't get the wireless working soon I'm in big trouble so any help would be great, preferably in words of two syllables or less as I'm not much of a tech head!! 

Thanks

---

### Post by ugm6hr on 2010-08-03
I can confirm the BCM4312 works flawlessly with Ubuntu 10.04. It's the device used in the Mini 9 too (which I have).

From a fresh install:
[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

If that doesn't work, and lshw suggests it is switched off, it may be a hardware switch, BIOS switch, or perhaps Windows left it in a power saving mode, from which ubuntu can't re-enable (see Wifi help link below for details of the last).

---

### Post by pebeo on 2010-08-04
Thanks! it seems it may have been working anyway but i hadn't switch it on manually (its not my laptop, mine has a little light to tell me these things) but i did the fresh install anyway and turned it on and its working now!

---

### Post by utilitytrack on 2010-08-04
please mark this thread as solved

---

