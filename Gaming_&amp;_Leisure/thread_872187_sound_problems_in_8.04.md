---
title: "sound problems in 8.04"
date: 2008-07-27
forum: Gaming &amp; Leisure
---

### Post by hotballz87 on 2008-07-27
so i recently installed ubuntu 8.04, upgrading from 7.10, and i am now having the same problem i had in 7.04, i can have only one program with sound at once, everything that runs under it will not output any sound at all. i cant remember what i did to fix this before, and im guessing it might be different.
anyone have this problem, or ideas on how to fix it??

---

### Post by Vakman on 2008-07-27
Sound card? Please post the output of
```
lspci
```

---

### Post by hotballz87 on 2008-07-27
```
00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
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
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

its an onboard card, im not sure what it is

---

### Post by Vakman on 2008-07-27
You now know your sound card. That is why I had to post that output :lolflag:
**Edit**: I have heard of this helping. Enter this and let me know if it works or not go to System > Preferences > Sounds and uncheck the box that says "Enable software sound mixing."

---

### Post by hotballz87 on 2008-07-27
i turned that off, and nothing worked, so i started messing with all the hardware crap in the sound options, and got it to work by switching everything to ALSA instead of autodetect.....

i feel dumb on how easy it was...

---

### Post by Vakman on 2008-07-27
:lolflag:
Well at least it works now. I had in a code box earlier for something to switch everything to ASLA but in an edit I took it out because I didn't think it would help.
Anyway, it works is the point.

---

