---
title: "Enabling sli"
date: 2007-02-14
forum: Gaming &amp; Leisure
---

### Post by Plosky on 2007-02-14
I am trying to configure a sli setup for both of my 6600gt Nvidia graphic cards but I am experiencing some troubles.  Of course, I enabled the Sli option in my Xorg.conf file but I think the roblem resides in the pci bridge. Personnaly I believe that the pci bus brigde is not well recognised because  of the output of the following commands.  Any help to  further analyse my situation would be greatly appreciated.  Enabling double gpu is the only thing stopping me from totally removing windows of my system.

Thank you for your consideration

The following commands had this output :

> $ lspci | grep -i nvidia

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)


$ lspci -tv
-[0000:00]-+-00.0  nVidia Corporation CK804 Memory Controller
           +-01.0  nVidia Corporation CK804 ISA Bridge
           +-01.1  nVidia Corporation CK804 SMBus
           +-02.0  nVidia Corporation CK804 USB Controller
           +-02.1  nVidia Corporation CK804 USB Controller
           +-04.0  nVidia Corporation CK804 AC'97 Audio Controller
           +-06.0  nVidia Corporation CK804 IDE
           +-07.0  nVidia Corporation CK804 Serial ATA Controller
           +-08.0  nVidia Corporation CK804 Serial ATA Controller
           +-09.0-[0000:05]--+-06.0  Creative Labs SB0400 Audigy2 Value
           |                 +-0b.0  Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
           |                 \-0c.0  Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller
           +-0a.0  nVidia Corporation CK804 Ethernet Controller
           +-0b.0-[0000:04]--
           +-0c.0-[0000:03]--
           +-0d.0-[0000:02]----00.0  nVidia Corporation NV43 [GeForce 6600 GT]
           +-0e.0-[0000:01]----00.0  nVidia Corporation NV43 [GeForce 6600 GT]
           +-18.0  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
           +-18.1  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
           +-18.2  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
           \-18.3  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control


---

