---
title: "Vostro 1000 hardware detections"
date: 2009-01-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Byr0n_X on 2009-01-05
Hi. I have a vostro 1000 width Ubuntu 8.10 and need some help to make my card reader work and some kind of fan control. Thanks.

---

### Post by epitaph on 2009-01-06
The SD card reader works fine out of the box for me on the Vostro 1000, are you sure it's an issue with the reader itself and not the SD card?

What issues with fans are you having? Mine runs when it's necessary, just as it did in Vista.

---

### Post by Byr0n_X on 2009-01-06
Hi, Its funny im my Vistro the card reader never works in Ubuntu but, in Windows it's works good.

Take a look in my "lspci"

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

Tanks for the reply.

---

### Post by Unparallelogram on 2009-01-06
Having bought a Vostro 1000 slightly under two years ago, I believe that Dell has actually been reusing the model number for different and largely unrelated systems. The computer I own differs from what Dell's website was selling as Vostro 1000 more recently a while back. That said, my card reader also works out of the box the last time I checked. It's just all the other issues I dislike.

EDIT: Found my camera. It works indeed.
EDIT2: lspci shows the following line, among others:
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
which is the same as yours... strangely.

---

### Post by epitaph on 2009-01-06
```
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
```

I have the same one. It works great. AWN even gives it a cute little SD/MMC icon on my dock.

I'm not really sure where to start with troubleshooting it. Sorry.

I am using 8.04.1 64-bit, not 8.10.

Unparallelogram: I've managed to overcome most issues with my Vostro 1000. Which issues or unwanted behavior are you having? I might be able to help/provide a solution for them.

---

