---
title: "GNOME Windows Stops Responding"
date: 2011-06-28
forum: Desktop Environments
---

### Post by try1t on 2011-06-28
I'm having a major problem with my Ubuntu 11.04 desktop environment, GNOME.

My windows seem very unresponsive and lag a lot when moved around. Sometimes they literary start flashing and don't respond to my inputs during the short, but very much repetitive, flash periods. This follows the primary window, so that when I change window the new window starts flashing. I use the drivers from NVIDIA's homepage due to thinking they might solve the problem - they didn't. 

Parts of the screen also pops up where my pointer is located and windows stick to my pointer when I just click them once, as if I want to drag them around.

I myself think this is a problem with the NVIDIA drivers or GNOME, but can't figure out what the problem's source is.

```

lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GF110 [Geforce GTX 570] (rev a1)
01:00.1 Audio device: nVidia Corporation GF110 High Definition Audio Controller (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation GF110 [Geforce GTX 570] (rev a1)
02:00.1 Audio device: nVidia Corporation GF110 High Definition Audio Controller (rev a1)
04:00.0 SATA controller: Marvell Technology Group Ltd. Device 9120 (rev 12)
05:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 04)
06:00.0 USB Controller: Device 1b6f:7023 (rev 01)
07:00.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
08:01.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
08:04.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
08:05.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
08:06.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
08:07.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
08:08.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
08:09.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
09:00.0 USB Controller: Device 1b6f:7023 (rev 01)
0a:00.0 PCI bridge: Device 1b21:1080 (rev 01)
0c:00.0 USB Controller: Device 1b6f:7023 (rev 01)
0d:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0e:00.0 SATA controller: Marvell Technology Group Ltd. Device 9120 (rev 12)
0f:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```Do you know how to solve this? I'm a noob - please don't kill me, I'm too young! :rolleyes:

---

