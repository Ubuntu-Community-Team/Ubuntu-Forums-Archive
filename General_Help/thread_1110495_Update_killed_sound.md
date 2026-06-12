---
title: "Update killed sound"
date: 2009-03-29
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2009-03-29
So I've been searching all over the internets for a reasonable solutions to 2 problems and found nothing. The problems occurred right after an update of the kernel headers for 2.6.24.24. Something in that update changed me over from 2.6.24-24-rc to 2.6.24-24-386 and took away nvidia 6150 nforce 430 support. I rectified the graphics issue by reinstalling nvidia glx drivers but the second issue, unresolved, was my sound. I rebooted into a windows partition and sound works great. Tried reinstalling alsa and gstreamer to no avail, oss wont install, and lspci is telling me nothing except that it sees the device.

```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
01:0a.0 Multimedia video controller: Conexant CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
```

Not real sure what to make of this...

Edit: Just found that gnome-settings-daemon isnt working either. Could this be an issue involving the sound? I tried to fix this via info from the bug reporting sites 
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/188010](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/188010)  but got nothing. Everything was already as requested in the issue's "fix".

```
Killmandline:+$ gnome-settings-daemon

** (gnome-settings-daemon:6527): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:6527): WARNING **: Could not acquire name
```

---

### Post by Sin@Sin-Sacrifice on 2009-03-29
Anything?? Anyone??

---

### Post by Sin@Sin-Sacrifice on 2009-03-29
Ha... well.. dumb stoner mistake again. Just finally got fed up and was about to walk away when I thought about the modules for the kernel. I remembered that uname -a told me that the kernel was 2.6.24-24-rt before the upgrade and just recently the command told me 2.6.24-24-386, got to thinking and realized that I might not have them modules and low and behold... I have sound once again.

---

