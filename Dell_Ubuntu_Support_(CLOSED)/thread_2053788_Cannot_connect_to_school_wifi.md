---
title: "Cannot connect to school wifi"
date: 2012-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Simmyslim on 2012-09-06
I have a Dell Latitude D531 and i've been trying to connect to the wifi at my university. I can connect to the guest network, and my password protected network at home. But when I connect to the schools network i have to delete it first, then type my username, pw, etc. Then i get internet for maybe 3 minutes, then it stops loading pages. Sometimes it crashes too. Then if i want to get 3 more minutes i have to delete the network again and rinse and repeat. My schools network uses a WPA/TKIP encryption. I'm brand new to ubuntu so if you want to see any codes or something just tell me what to do and i'll post whatever. I followed this guide: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) to get my wireless card to work. Much obliged.

-Simen

---

### Post by mikewhatever on 2012-09-08
There are lots of suggestions in the thread you've followed, have you installed ndisrapper?  If so, I'd suggest removing it and trying one of the native drivers as suggested in some of the latest posts. The native drivers haven't worked well back in 2006, but have improved greately by 2012.

In case you need help troubleshooting, please post the usual outputs like

lspci -nnk | grep -iA2 net

lsmod

---

### Post by kurt18947 on 2012-09-09
Like Mike Whatever, I'd suspect driver issues.  Perhaps post the output of the command 
```
lspci
``` assuming this is a 'built-in' wifi adapter.  You may see a line similar to this:

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

That line tells me what kind of wifi chipset I have.  Certain chipsets have certain known problems and there are usually workarounds.

---

### Post by Simmyslim on 2012-09-10
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
```

---

### Post by ugm6hr on 2012-09-15
```
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
```

There are 2 driver options for BCM wifi cards. Some work better with one - some better with others.

I have had the exact same problem with WPA on my BCM wifi netbook - repeated dropping of signal requiring turning off wifi and turning back on.

Check what driver you are using with:
```
lshw -c network
```

The option are wl and sta - try using the other one.

---

