---
title: "Dell D630 Dual Monitors with Dock"
date: 2011-08-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rickyjones on 2011-08-26
Hello,

I'm trying to resolve an annoying issue that I have with my laptop. It is a Dell D630 running Ubuntu 11.04 64bit. I'm using the Dell D/Port Advanced Port Replicator on my desk so that I can just place my laptop and have it work with my keyboard/mouse and dual 22in monitors.

My primary monitor is connected to the DVI port. The secondary monitor is connected to the VGA port.

If I place my laptop into the dock with it closed then I never receive a valid signal to the monitors. I need to open my laptop screen then I usually get something. However every time I undock and redock I need to spend a few minutes completely re-configuring the dual desktop configuration. Often I'll have the same image across all three monitors... I hate to make comparisons, but this behavior was flawless in Windows 7, and I'd like to replicate that behavior. On the flip side, removing the laptop to go work elsewhere never results in an issue.

Most everything is still the default install. No extra drivers are being used. 

My goal is to be able to place my laptop into the dock with the screen closed, turn it on, and have the primary image on the DVI monitor and then extend the desktop to the other monitor. When I undock (after suspending the laptop) I want the laptop screen to be the only monitor.

Any help would be greatly appreciated. Trying to make the jump from Windows to Ubuntu on my primary workstation and this is just a major annoyance! Thank you :-)

Here is the output from lspci to answer any questions on the hardware in use:

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

Attached is the output from the lshw command, for a more detailed look at the hardware.

Thanks,
Richard

---

### Post by benj.mull on 2011-09-29
I have the same configuration but with Dual Dell 2007FPb monitors and am unable to get them working at all.  The monitors display Out of Range messages.  Any help would be appreciated.  This used to work with 10.10.

---

