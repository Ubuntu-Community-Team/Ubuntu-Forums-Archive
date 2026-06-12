---
title: "wmii slower than gnome with compiz!?"
date: 2009-11-22
forum: Desktop Environments
---

### Post by cwik on 2009-11-22
I've been very keen on trying a tiling window manager, and have settled on wmii for now.  When switching between views (sorta analogous to workspaces) it takes far longer to render in wmii comparted to gnome with compiz settings on.  By far longer, I mean it seems instantaneous on gnome, while it takes around 3 seconds in wmii.  Installing wmii also installed dwm, which *is* fast and snappy, but I'm under the impression that dwm requires recomplies, and isn't as simple to congfigure as wmii.

Opening new terminals also takes longer in wmii than gnome with compiz, so it's not just switching between views/workspaces.

I installed wmii using the default ubuntu repositories (apt-get wmii got me wmii3) on a completely fresh 9.10 installed (i386).

I'm on an IBM ThinkPad T41p.  Here's my lspci:
```

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

```

I have not modified xorg.conf.  In fact, it's not even in /etc/X11/ where I expect to find it (I'm assuming something changed between 9.04 and 9.10).  In Gnome, I do not have any proprietary drivers installed, and it does not prompt me to install any.

Any help or pointers would be much appreciated!

Please bear with me, I've rarely posted before, so sorry if I forget to include obvious things like logs or settings.

---

