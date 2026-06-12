---
title: "Gnome Panel Doesn't Update Using Compiz Fusion"
date: 2010-09-13
forum: Desktop Environments
---

### Post by mannequin on 2010-09-13
Hi all,

I want to use Compiz Fusion instead of Metacity, but there is one thing that is (and has in the past) stopping me from using it.  There are times when Gnome Panel won't update until I switch to a different workspace and then back.  What I mean by "won't update" is that the time will stay at say 6:20p, the window list stays the same whether windows are opened or closed, etc.  It's like the panel is frozen in time.

Has anyone had this problem and is there a fix?

Thanks!
-M.

---

### Post by ajgreeny on 2010-09-13
Sounds to me like a graphics driver problem.  What hardware?  Let's see the output of ```
lspci
``` and/or ```
lshw -c display
```

---

### Post by mannequin on 2010-09-14
lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

lshw -c display (not as a super user):
```
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: Radeon Mobility X1400
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:16 memory:d0000000-dfffffff(prefetchable) ioport:ee00(size=256) memory:efdf0000-efdfffff memory:efe00000-efe1ffff(prefetchable)

```

Thanks for whatever help you can give as I'm lost and I have been searching Google for a dew days.  :)

-M.

---

### Post by ajgreeny on 2010-09-14
Are there any drivers available in System -Administration -Hardware Drivers?  If not you are stuck with the radeon driver currently used and may need to try a manual edit of /etc/X11/xorg.conf, which may not even exist at the moment.

I have to do a similar thing for my ATI 9200SE card that makes it run at 16 bit colour to get better performance from it.

---

### Post by mannequin on 2010-09-15
I am stuck with the Radeon driver as the x1400 isn't supported by ATI / AMD anymore.  I have downloaded a DEB with one of the latest Radeon drivers which improved speed.

But, I don't think this problem is with the drivers as it was with both the proprietary and free drivers.  I was hoping the problem would be a setting with Compiz, because it caused the same problem with KDE when I was trying it out recently.

-M.

---

