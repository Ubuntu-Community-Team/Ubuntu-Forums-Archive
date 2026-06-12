---
title: "Konsole text overwritten not cleanly refreshed"
date: 2008-05-15
forum: Desktop Environments
---

### Post by karye on 2008-05-15
Help! What's the problem here? I searched forum and google without result..

[IMG]http://files.kuroo.org/Konsole.png[/IMG]

As you see in the dump text is written over and not cleanly refreshed.
This affects all types of applications: Konsole, Pidgin etc..
The graphics card is a Nvidia GeForce 6600 with latest 169.12 driver on x86   Heron install and cpu amd64.

The relevant xorg.conf is:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony SDM-S73"
    HorizSync       28.0 - 65.0
    VertRefresh     57.0 - 75.0
EndSection

Section "Device"
    Identifier     "VideoCard0"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 6 Series"
    BusID          "PCI:5:0:0"
    Screen          0
    Option          "NoLogo"        "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "VideoCard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024@60 +0+0; 1280x960@60 +0+0; 1024x768@60 +0+0; 1024x768@70 +0+0; 1024x768@75 +0+0; 832x624@75 +0+0; 800x600@60 +0+0; 800x600@75 +0+0; 800x600@72 +0+0; 640x480@75 +0+0; 640x480@72 +0+0; 640x480@60 +0+0"
EndSection

```

Here's the output of lspci:
```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
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
01:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)

```

---

### Post by Zorael on 2008-05-15
I had this as well, also when using Nvidia's proprietary drivers, but only when running Compiz. After upgrading Compiz to an unstable version from git, using [this script](http://ubuntuforums.org/showthread.php?t=781218), it (mostly) went away. If it only happens with compiz running, you could try doing the same and see if it improves. It's easy enough to uninstall.

See [http://forum.compiz-fusion.org/showthread.php?t=6742](http://forum.compiz-fusion.org/showthread.php?t=6742). There are some suggestions as to options you could put into your xorg.conf to supposedly make it better. I didn't have much luck with those. (Though I did keep TripleBuffering.)

Of course, the git builds aren't bug-free either, but I haven't experienced this particular one since then.

---

