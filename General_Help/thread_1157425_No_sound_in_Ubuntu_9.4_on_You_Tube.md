---
title: "No sound in Ubuntu 9.4 on You Tube"
date: 2009-05-12
forum: General Help
---

### Post by Rodhill on 2009-05-12
I cant get the sound to work when on You Tube. I can hear the start up sound when I start Ubuntu 9.4 ok.
Can someone help? Everything was fine in 8.04.

Thanks 

Rod

---

### Post by jimbob on 2009-05-12
Type ***[COLOR="Blue"]sudo alsamixer[/COLOR]*** in a terminal window and make sure the master volume is turned up into the red area.

---

### Post by Rodhill on 2009-05-13
> **jimbob said:**
> Type ***[COLOR="Blue"]sudo alsamixer[/COLOR]*** in a terminal window and make sure the master volume is turned up into the red area.

Hi Jimbob, yes it's turned up full. I can play music fine from cd and hear the Ubuntu start up sound ok. It's only off in You Tube.It was ok in 8.04 until I upgraded.

Rod

---

### Post by Rodhill on 2009-05-13
This is my sound card details:-

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev 

Rod

---

### Post by Rodhill on 2009-05-13
Problem sorted!:) I uninstalled and re-installed the flash player. Then re-started Firefox.

Thank you.

---

### Post by yuki86 on 2009-05-13
for me helped, when I install new version 10 incited system preinstalled 9

---

