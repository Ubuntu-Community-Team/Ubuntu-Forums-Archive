---
title: "Steam crash after login"
date: 2019-04-15
forum: Gaming &amp; Leisure
---

### Post by couter0 on 2019-04-15
I'm a bit new into this, but anyway...
 
 I have Ubuntu 18.04 64-bits, on a "cheap" computer, it's not the best but it's something, the hardware info is (or i think it is):

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation NV44 [GeForce 6200 TurboCache] (rev a1)
02:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)

 The problem is that, when i start steam and log-in it just crashes. and this is what it says when launched by terminal:

Running Steam on ubuntu 18.04 64-bit
STEAM_RUNTIME is enabled automatically
Pins up-to-date!
[2019-04-13 19:24:22] Startup - updater built Feb 18 2019 22:08:53
Looks like steam didn't shutdown cleanly, scheduling immediate update check
[2019-04-13 19:24:24] Checking for update on startup
[2019-04-13 19:24:24] Checking for available updates...
[2019-04-13 19:24:24] Downloading manifest: client-download.steampowered.com/client/steam_client_ubuntu12
[2019-04-13 19:24:26] Download skipped: /client/steam_client_ubuntu12 version 1550534751, installed version 1550534751
[2019-04-13 19:24:26] Nothing to do
[2019-04-13 19:24:26] Verifying installation...
[2019-04-13 19:24:26] Performing checksum verification of executable files
[2019-04-13 19:24:30] Verification complete
<user>@<username>$

help..?

---

### Post by oldrocker99 on 2019-04-15
Did you download from the Steam webpage? 

If you did,  remove the current installation of Steam. Scroll down for the Linux instructions: [https://www.wikihow.com/Uninstall-Steam](https://www.wikihow.com/Uninstall-Steam)

If you **did** install from the repos, look here: [https://github.com/ValveSoftware/steam-for-linux/issues/5463](https://github.com/ValveSoftware/steam-for-linux/issues/5463)

```
sudo apt install steam
```

This pulls in a raft of dependencies, so it should run fine & dandy.

---

