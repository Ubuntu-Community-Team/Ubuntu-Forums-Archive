---
title: "Need help resume from suspend is not working."
date: 2012-10-25
forum: Desktop Environments
---

### Post by NetGO on 2012-10-25
I tried to debug this issue more than a month. I need help!

Suspend looks fine. But resume fails, pm-suspend does now show any wake messages.

Suspend then led blinking, if I press keyboard, fan starts but nothing happens. So I have to cold boot.  If I turn off my pc by just pressing power buttin long, I cannot boot from power button again, just fan works and nothing. So I have to turn off main psu switch then boot.

pm-suspend.log shows nothing about wake up. suspend looks fine though.

Tested S1 suspend and it works. But pm-hibernate, I cannot resume either. I need S3 suspend because fan is still alive in case of S1 suspend.

Installed 12.10 amd64 desktop.

Can someone help me?

I am attaching lspci message. Motherboard is supermicro H8DCE and has 16gb registered ecc memory. 2x opteron 285 processors. Graphic card is ATI HD4350

00:00.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: NVIDIA Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: NVIDIA Corporation CK804 SMBus (rev a2)
00:02.0 USB controller: NVIDIA Corporation CK804 USB Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: NVIDIA Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: NVIDIA Corporation CK804 IDE (rev f2)
00:08.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: NVIDIA Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: NVIDIA Corporation CK804 Ethernet Controller (rev f3)
00:0d.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Radeon HD 4350]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series]
80:00.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a3)
80:01.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev f3)
80:08.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
80:0a.0 Bridge: NVIDIA Corporation CK804 Ethernet Controller (rev f3)
80:0d.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev f3)
80:0e.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
81:00.0 PCI bridge: PLX Technology, Inc. PEX 8648 48-lane, 12-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev bb)
82:04.0 PCI bridge: PLX Technology, Inc. PEX 8648 48-lane, 12-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev bb)
82:05.0 PCI bridge: PLX Technology, Inc. PEX 8648 48-lane, 12-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev bb)
82:08.0 PCI bridge: PLX Technology, Inc. PEX 8648 48-lane, 12-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev bb)
82:09.0 PCI bridge: PLX Technology, Inc. PEX 8648 48-lane, 12-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev bb)
83:00.0 RAID bus controller: HighPoint Technologies, Inc. Device 2760 (rev 03)
84:00.0 RAID bus controller: HighPoint Technologies, Inc. Device 2760 (rev 03)
85:00.0 RAID bus controller: HighPoint Technologies, Inc. Device 2760 (rev 03)

---

