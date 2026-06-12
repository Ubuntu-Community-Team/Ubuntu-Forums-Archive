---
title: "Dimension e520 - resolution help!"
date: 2007-09-12
forum: Dell  Ubuntu Support
---

### Post by gurdy on 2007-09-12
I got the e520 running Ubuntu, with onboard Intel g965 graphics.
I can't get the 1440x900 resolution to display correctly on the syncmaster monitor.
I'm dual-booting with XP (I blew away ubuntu, installed xp and re-installed unbuntu), and after downloading the right Intel driver I got the resolution working in XP.
But I can't get the resolution working in ubuntu!

I tried the "gtf 1440 900 60" method and changed xorg.conf to:

Section "Monitor"
Identifier "SyncMaster"
Option "DPMS"
# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
EndSection

But no such luck--instead of a stretched screen I now have a squished screen. Heh.

Any suggestions?

---

### Post by phr0ze on 2007-09-12
I dont use modelines. Most of the time you can fix this by looking up your monitor's true vertical and horizontal sync rates. Then edit your config file as follows.

Type or copy the following into a command line assuming you are using Ubuntu and not kubuntu, etc.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bak

gksudo gedit /etc/X11/xorg.conf

Edit this file. In the monitor section near the bottom you will see Vertrefresh and Horizsync. Update these values to the ones provided by the monitor spec sheet.

Then in the Screen section go down to the display section for 24bit depth and add the resolutions you would like in front. Such as
Modes "1680x1050" "1024x768" "800x600"

You can edit the other depth sections too but it is unlikely you will run at less than 24bit.

Save the file and reboot.

---

