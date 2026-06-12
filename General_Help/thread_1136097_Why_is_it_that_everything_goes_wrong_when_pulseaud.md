---
title: "Why is it that everything goes wrong when pulseaudio is running?"
date: 2009-04-24
forum: General Help
---

### Post by dragos240 on 2009-04-24
And why is it that when I end it, everything works. It's very frustrating, it's happened more and more often! Why is pulseaudio torturing me so???

---

### Post by paradigm2 on 2009-04-24
> **dragos240 said:**
> And why is it that when I end it, everything works. It's very frustrating, it's happened more and more often! Why is pulseaudio torturing me so???

PulseAudio is a known troublespot right now in Jaunty.

Did you upgrade or do a clean install?

-If upgrade, you may try deleting your ~/.pulse directory and rebooting.

-If this does not work and you want it fixed, you might consider upgrading pulseaudio and alsa using a PPA:

[https://launchpad.net/~themuso/+archive/ppa/](https://launchpad.net/~themuso/+archive/ppa/)

Note: The above is not official Ubuntu.  If you are willing to wait an indefinite time (maybe days, maybe weeks or months?), it will probably be provided eventually as a backport as well.

- What hardware do you have?

```

lspci

```

Intel HDA cards have particularly been having problems which seem to need a [unofficial from mainline repository] kernel upgrade to 2.6.30rc2 or later to resolve.

---

### Post by dragos240 on 2009-04-24
> **paradigm2 said:**
> PulseAudio is a known troublespot right now in Jaunty.

Did you upgrade or do a clean install?

-If upgrade, you may try deleting your ~/.pulse directory and rebooting.

-If this does not work and you want it fixed, you might consider upgrading pulseaudio and alsa using a PPA:

[https://launchpad.net/~themuso/+archive/ppa/]("https://launchpad.net/%7Ethemuso/+archive/ppa/")

Note: The above is not official Ubuntu.  If you are willing to wait an indefinite time (maybe days, maybe weeks or months?), it will probably be provided eventually as a backport as well.

- What hardware do you have?

```

lspci

```Intel HDA cards have particularly been having problems which seem to need a [unofficial from mainline repository] kernel upgrade to 2.6.30rc2 or later to resolve.

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
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:06.0 Communication controller: Conexant Systems, Inc. Device 2f40
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
```

---

### Post by dragos240 on 2009-04-24
The deleting of the .pulse folder seemed to help. Although only time will tell!

---

