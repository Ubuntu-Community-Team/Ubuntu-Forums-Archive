---
title: "Help With Getting Wireless Card Working"
date: 2009-03-02
forum: General Help
---

### Post by crapple on 2009-03-02
I have the hp m9357c.  [http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2100&lc=en&dlc=en&cc=us&lang=en&product=3774377]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2100&lc=en&dlc=en&cc=us&lang=en&product=3774377") How do I get the wireless card working it dose not show up in restricted drivers.  It is not in network manger.  I am running ubuntu 8.10 any ideas.

---

### Post by avtolle on 2009-03-02
Do you know which wireless card you have? From the command line, do```
lspci
``` and post the results, please.

---

### Post by crapple on 2009-03-02
This is the output

```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:06.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:00.0 VGA compatible controller: nVidia Corporation Device 06e0 (rev a1)
03:00.0 Network controller: RaLink Device 0781
04:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 0f)

```

---

### Post by avtolle on 2009-03-02
From [http://ubuntuforums.org/showthread.php?t=708499](http://ubuntuforums.org/showthread.php?t=708499) looks like you'll have to d/l and compile the driver for your RaLink card.

---

### Post by crapple on 2009-03-02
I am not really sure how to do this and I think I have a different card number.

---

### Post by crapple on 2009-03-03
can anyone explain how to install this driver

---

