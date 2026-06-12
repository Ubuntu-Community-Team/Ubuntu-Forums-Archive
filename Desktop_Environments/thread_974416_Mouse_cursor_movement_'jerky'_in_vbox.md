---
title: "Mouse cursor movement 'jerky' in vbox"
date: 2008-11-07
forum: Desktop Environments
---

### Post by TikiKai on 2008-11-07
Hello, I have a couple of apps I can't get running in wine, so I installed vbox granting XPSP3 a full gig of ram (There are 4 in the workstation.

When I launch it, all indicators seem to show the machine running very well, but the mouse movement is horribly unusable. It moves very 'sticky' so if I move it across the screen it goes in jerks rather than smoothly. It IS a USB mouse, and from what I have read, there are issues with usb and virtual box so this may be the issue.It is a real shame that I really use these two apps and need to install a vbox at all, since I just made a 100% move to linux with a couple of Debian boxes and 3 Ubuntu machines but the fact is that I need both of them.

Is there a file I can edit to take care of this? I it makes any diff, I'm on intrepid and everything us u to date. lspci shows:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)




Thanks.

---

### Post by theduffman on 2008-11-07
> **TikiKai said:**
> Hello, I have a couple of apps I can't get running in wine, so I installed vbox granting XPSP3 a full gig of ram (There are 4 in the workstation.

When I launch it, all indicators seem to show the machine running very well, but the mouse movement is horribly unusable. It moves very 'sticky' so if I move it across the screen it goes in jerks rather than smoothly. It IS a USB mouse, and from what I have read, there are issues with usb and virtual box so this may be the issue.It is a real shame that I really use these two apps and need to install a vbox at all, since I just made a 100% move to linux with a couple of Debian boxes and 3 Ubuntu machines but the fact is that I need both of them.

Is there a file I can edit to take care of this? I it makes any diff, I'm on intrepid and everything us u to date. lspci shows:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)




Thanks.
cant help you with the vbox issue im afraid ive had to ditch it cuz of usb, what are the apps you need? Wine might not work but have you tried crossover office?  does a little better job than wine for some apps..just a thought.

---

### Post by TikiKai on 2008-11-07
Thanks Duff, I looked at Crossover and it doesn't cut it either... The apps are SiteSpinner which I use on some web sites, and one called Utopia Angel which I use to calculate stuff for a game I play online.

I appreciate the feedback, though!

Best regards!

---

