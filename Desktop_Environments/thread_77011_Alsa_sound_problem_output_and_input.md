---
title: "Alsa sound problem output and input"
date: 2005-10-16
forum: Desktop Environments
---

### Post by joanverde on 2005-10-16
I have sound with theh alsa system but it's just a big noise when you
test it from the Multimedia systems selector, and in amarok you can hear something that is supposed to be the track but under a layer of big scratchy noise.

ESD and arts can't build pipelines and OSS doesn't any sound at all.

While trying to test the input for alsa no pipline could be built.

How to solve these issues?

---

### Post by joanverde on 2005-10-16
To add I have one soundcard on the motherboard and one external through usb, neither of them works and now an alsa pipeline couldn't be built neither.

---

### Post by joanverde on 2005-10-16
some more info, here is my lspci with the usb soundcard choosen.

lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0204
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1204
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2204
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3204
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4204
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7204
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]
0000:00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 46)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Co ntroller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3 108 (rev 01)

---

