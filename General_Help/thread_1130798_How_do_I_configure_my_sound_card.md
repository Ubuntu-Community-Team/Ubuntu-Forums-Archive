---
title: "How do I configure my sound card?"
date: 2009-04-20
forum: General Help
---

### Post by davidianstyle on 2009-04-20
I just installed Kubuntu Linux on a separate partition (in addition to Windows Vista) and aside from sound and video problems, everything seems to be running smoothly. My speakers are plugged into the audio out jack (on the motherboard), which works fine in Vista, but isn't working in Kubuntu...

Here are my system specs:
Processor: 4x Intel(R) Core(TM)2 Quad CPU Q9650 @ 3.00GHz
Memory: 3111MB
Resolution: 1920x1200px
OpenGL Renderer: Software Rasterizer
X11 Vendor: The X.Org Foundation
Kernel: Linux 2.6.27-11-generic (i686)
Video Card: ATI Technologies Inc Mobility Radeon HD 3450

$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

I'm not sure what to do next...

I'd really appreciate if someone could help!

Thanks,
David

---

### Post by celthunder on 2009-04-20
do you have alsa or oss? run alsamixer in a terminal and make sure nothings muted (master is muted by default).

---

