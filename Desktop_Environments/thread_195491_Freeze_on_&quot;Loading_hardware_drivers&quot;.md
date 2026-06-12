---
title: "Freeze on &quot;Loading hardware drivers&quot;"
date: 2006-06-12
forum: Desktop Environments
---

### Post by swingincelt on 2006-06-12
I seem to have a similar issue to this thread which doesn't seem to come to a definitive conclusion:
[http://www.ubuntuforums.org/showthread.php?t=167722](http://www.ubuntuforums.org/showthread.php?t=167722)
The bootup process will freeze (keyboard unresponsive) on "Loading hardware devices" when I turn on the computer (after it has been off overnight).  After a reset/reboot, it will boot fine.

Some suggestions on diagnosing the problem would be helpful.

ASUS a7nx-d motherboard
AND 2700 XP

Here's lspci:
```
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 AudioControler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:01:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
0000:02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
0000:03:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)
```

---

