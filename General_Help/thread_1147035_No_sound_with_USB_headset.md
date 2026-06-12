---
title: "No sound with USB headset"
date: 2009-05-03
forum: General Help
---

### Post by shade11 on 2009-05-03
I have a friend who is trying to get his "c-media usb headphone set" to work under Ubuntu 9.04. After many attempts at getting it to work, it still doesn't. Any help would be appreciated.

lspci
```
00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)

00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)

00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)

00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)

00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)

00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)

00:03.3 Co-processor: nVidia Corporation MCP73 Co-processor (rev a2)

00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)

00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)

00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)

00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)

00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)

00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)

00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)

00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)

00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)

00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)

02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
```

asoundconf list
```
Names of available sound cards:

NVidia

defa
```

---

