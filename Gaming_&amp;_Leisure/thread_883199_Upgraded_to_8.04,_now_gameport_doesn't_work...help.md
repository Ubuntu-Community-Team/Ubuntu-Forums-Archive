---
title: "Upgraded to 8.04, now gameport doesn't work...help!"
date: 2008-08-07
forum: Gaming &amp; Leisure
---

### Post by harlock74 on 2008-08-07
So this is what is happening.  I upgraded my system to 8.04 and now my gamepad (Sidewinder doesn't work). It was working 100% under 7.04.  Right if I ls /dev/input I see a js0 there. I get this from different things:

cat /dev/input/js0 
cat: /dev/input/js0: No such device

lsmod | grep gameport
gameport               16008  4 analog,sidewinder,ns558,snd_cmipci


lspci
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0c.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)


I've reworked various How-to's for gameport/gamepads, but still, the main problem is the /dev/input/js0 not "existing"...

any ideas?  Thanks!

Note:  Gameport is in a SoundBlaster card.  Sound works 100% on system.

---

### Post by harlock74 on 2008-08-10
anyone?

---

### Post by lotus160 on 2008-11-11
I have exactly the same problem with a C-Media CM8738 sound card. I've spent days tries to work this one out.
Anyone got any suggestions?



Tony

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

---

