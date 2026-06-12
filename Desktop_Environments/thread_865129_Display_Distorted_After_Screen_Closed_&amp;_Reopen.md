---
title: "Display Distorted After Screen Closed &amp; Reopened"
date: 2008-07-20
forum: Desktop Environments
---

### Post by rlondre on 2008-07-20
My display is extremely distorted after the screen is closed and reopened. When I had windows the small button that is depressed upon closing the laptop would cause the computer to hibernate. However, now with ubuntu, closing the screen causes the display to become noting but black with a few lines and colors and oddly enough only the mouse pointer is visible. Every time I close the screen I need to hard shut down and reboot to fix the display. Is there a way to assign a function to the small button like with windows or someway to just stop this problem from hapening?

---

### Post by overdrank on 2008-07-20
> **rlondre said:**
> My display is extremely distorted after the screen is closed and reopened. When I had windows the small button that is depressed upon closing the laptop would cause the computer to hibernate. However, now with ubuntu, closing the screen causes the display to become noting but black with a few lines and colors and oddly enough only the mouse pointer is visible. Every time I close the screen I need to hard shut down and reboot to fix the display. Is there a way to assign a function to the small button like with windows or someway to just stop this problem from hapening?

Hi and welcome, there are many laptops that have issues with hibernating. Could you tell us some system specs? 

Also have you installed the graphics driver if needed?
You may also search the forums for you specific model to help.

---

### Post by rlondre on 2008-07-20
Here are my system specs, and no I didn't manually install a graphics driver. Where can I find a list of supported drivers that are available for 8.04LTS?

londre@londre-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
01:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

---

### Post by rlondre on 2008-07-20
It seems that i need to replace my current driver with a i810 driver to correct my problem. Now my question is where can I find drivers for graphics cards and how do i switch them?

---

### Post by overdrank on 2008-07-20
> **rlondre said:**
> It seems that i need to replace my current driver with a i810 driver to correct my problem. Now my question is where can I find drivers for graphics cards and how do i switch them?

Hi and the drivers should be included with the install but you can use synaptic manager to search and ensure. If so then you may just reconfigure your xorg. with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` you may also use the display config tool. ```
gksu displayconfig-gtk
```

---

