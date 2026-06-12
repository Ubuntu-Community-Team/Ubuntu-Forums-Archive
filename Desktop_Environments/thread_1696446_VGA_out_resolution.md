---
title: "VGA out resolution"
date: 2011-02-27
forum: Desktop Environments
---

### Post by shafiekd on 2011-02-27
Hi

I'm a newbie to Ubuntu, so please excuse any ignorance.

I have Ubuntu 10.04 LTS installed on my HP Compaq Presario CQ60.
Unfortunately the screen is busted & I'm using an external LCD.

It boots directly onto the LCD, but the resolution is 800x600 by default, the only other option is  640x480.

I'm assuming its using the VESA drivers for the graphics.

I've managed to temporarily fix the resolution to 1024x768 by running the following in terminal for every session:
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768_60.00
xrandr --addmode VGA1 1024x768_60.00
xrandr --output VGA1 --mode "1024x768_60.00"

I've added a document to /etc/init.d so that it may be loaded on startup, but it does not seem to work.

I think the problem might be the fact that when copy & paste the above commands in terminal (I load all of these commands in one go), i still need to press enter it to take effect.
So I think I'm missing something in the script.
Or maybe I have the commands in the wrong location to be loaded at boot?...

Below is my output for lspci command:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

I know that the commands work, but how do I edit it so that I can load it at startup without having the pressing 'enter' issue.

Thanks

---

