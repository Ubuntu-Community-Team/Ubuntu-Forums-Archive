---
title: "Dell XPS m1330 - Wireless started suddenly to work randomly (Intel 4965 )"
date: 2011-04-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sikshady on 2011-04-07
Hello, I Have Ubuntu 10.10 x64 on a Dell xps m1330 ( 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux) using a Intel 4965 wi-fi PCI card.

From one day to another the wi-fi started to work really bad, becoming not usable. I don't know why it happened suddenly, it could be is due to some of the automatic updates (I usually do the various updates when requested), but anyway this is the behavior:

[LIST]
[*]usually it connects then few seconds later it disconnects or it stay connected but Internet is not working
[*]really rarely it works for more than few seconds
[*] sometimes it asks me again to confirm the WPA password of the SSID
[/LIST]
 I'm sure it's not a problem of coverage/router because on Windows 7 x64 (I have dual boot) the wifi works perfectly.

Do you have any idea? It is making me really going crazy :(
Thank you a lot.

This is output of /usr/bin/lspci
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
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
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```I dont know if could be useful but this is the content of /etc/modprobe.d
```
root@sik-XPS-M1330:/home/sik# locate modprobe.d
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-watchdog.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/intel-5300-iwlagn-disable11n.conf
/etc/modprobe.d/nvidia-graphics-drivers.conf
/usr/share/man/man5/modprobe.d.5.gz
```

---

### Post by malegria on 2011-10-10
I have the same wireless card in a Sony Vaio laptop and on some old thread I read that installing some backport modules clears up the problem. It has worked for me. I am using Ubuntu 11.10 Oneiric Ocelot and I installed
```
linux-backports-modules-headers-oneiric-generic
```
The issue seems to have stopped for me.

---

