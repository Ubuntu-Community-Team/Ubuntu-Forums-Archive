---
title: "xorg.conf for dual monitors - 2 cards"
date: 2008-04-07
forum: Desktop Environments
---

### Post by skyhawk98 on 2008-04-07
I have an onboard intel card and a Silicon Image Sil1364 ADD2-N card (PCI Express).  One monitor is plugged into each card.  So far, I have the same thing displayed on both monitors.  I would like to get dual monitors set up to extend my desktop from 1 to the other.

I have followed instructions at:
[http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624)

Problem is I don't think I have the right BusID for the Silicon Image card.
Output of lspci:
00:00.0 Host bridge: Intel Corporation 82Q33 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q33 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q33 Express Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q33 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)

Is any of these the Silicon Image card?

---

