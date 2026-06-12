---
title: "Graphical freezes in Jaunty! (Due to nvidia drivers?)"
date: 2009-04-25
forum: General Help
---

### Post by Mike_IronFist on 2009-04-25
**EDIT: Switching to the NVIDIA 173 drivers seems to have solved the problem. Never mind.**


This is really the only problem I've had with Ubuntu that has persisted, at all. I get graphical freezes whiled doing various things whenever I have compiz enabled:

-Deleting stuff in the trash by highlighting a group of files and pressing "Delete"

-Creating a "manual launcher" for Cairo-Dock

-Sometimes just resizing windows

So essentially very random things. I've heard the problem is probably caused by the fact that nvidia's 180.44 drivers are awful and I should use a different version, or that I can use some kind of bugfix by adding a line to ~/.gnomerc . I don't know how to edit ~/.gnomerc since I have no idea where it is.

So I humbly ask for your help. Please help me stop this irritating freezing? (It's purely graphical - music keeps playing, discs keep burning, but the gui freezes and/or locks up entirely)


Here's what the lspci command told me:
```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200M G (rev a2)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

And before the less experienced users ask, I have more than enough RAM  (3 GB) and the video card drivers are correctly installed. Please do not bother me with rudimentary questions like that.

---

### Post by domnz on 2009-04-25
This is also happening to me, but for KDE. 

Random tasks, like starting a Skype call or trying to install Wine. Either the UI freezes completely or there is a black screen. Can't do anything except turn off the computer and start again.

Dell Dimension 5000.

Using the drivers applied during setup (Wubi).

---

### Post by compgeek83 on 2009-04-25
had same issue using open drivers that came by default, lol, finally got it to run long enough to install 180 drivers, no more freezeups!

---

### Post by domnz on 2009-04-26
Logically, I can't see that I can do anything more. If anyone has advice, let us know!

---

