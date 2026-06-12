---
title: "Slow scrolling and window dragging w/ 845G embedded graphics on Dell 2400"
date: 2012-03-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by B Dub on 2012-03-23
I have installed Lubuntu 11.10 (from CD) on my Dell Dimension 2400 desktop with 845G embedded graphics (intel extreme, I think it's called) and have noticed that shortly after I log in (maybe 2 minutes after) my screen freezes for a number of seconds and then once it regains responsiveness, window dragging and scrolling slows to a crawl.  The slowed dragging leaves a trail of gray boxes, and scrolling is just slow to respond.  In htop /usr/bin/X maxes out in CPU% any time I drag a window while this is happening (and gets close even when operating effectively).  I know that there is a lot of frustration out there when it comes to this chip set, but as it stands now this is what I have to work with.  

I have found that if I run xcompmgr from the lxterminal ("xcompmgr &") the graphics seem to work fine.  However, when I add an xcompmgr.desktop file to /etc/xdg/autostart/ with name and command set simply to "xcompmgr" (using lxshortcut) and reboot, I have the same issues and have to kill the process and then restart it from the terminal to get things working right again.  I have also tried using cairo-compmgr, which I like better due to its broader options and mousebindings for transparency, but have concluded begrudgingly that it simply won't work consistently with my system.

I noticed that my northbridge was running extremely hot to the touch (no temp sensor or thermometer here) and so regreased it with silicon thermal compound and added a little cpu fan for good measure.  It runs really cool now, but I still have these graphics issues.  MY questions:  1.  Why does xcompmgr seem to fix these issues and why do they only occur after I'm logged in for a couple minutes (not immediately)?  2.  Why do I have to load xcompmgr from the terminal, why is it screwing up when I add it to autostart?  3.  Should X be maxing out this way?  I didn't think dragging windows would be so CPU exhaustive.  4.  Does anyone out there have any experience with cairo-compmgr on a similar system?

Thanks for any and all assistance

Dell Dimension 2400 w/Intel Celeron 2.4GHz/400MHz FSB
lspci output:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by robbielink on 2012-06-13
I'm having this same issue since upgrading to Lubuntu 12.04 from Ubuntu 11.04 (I did a clean install, not an upgrade) yesterday. I have pretty much the same Dell machine you do. I'd had some issues with graphics in earlier Ubuntu versions. 11.04 seemed to fix them. I knew I couldn't use the new Gnome or Unity on this machine, though. 
So - Lubuntu with the LXDE desktop running Openbox (default installation). But after a few minutes I get the same issue as you - the slow dragging with multiple artifacts left behind. Sometimes the desktop goes black and then comes back on and rebuilds itself. I'll check logs when I get a chance a see if anything shows up there.

---

### Post by mikewhatever on 2012-06-15
Unfortunately, Intel's i8xx graphics chips are considered unsupported hardware. They used to work reasonably well untill about 2008 or so, but since then, they've been suffering from severe driver regretions that Intel has been unable or unwilling to fix.
More info: [https://wiki.ubuntu.com/X/i8xxUnsupported](https://wiki.ubuntu.com/X/i8xxUnsupported)

1. Not sure.
2. Probably because it starts before X does. Try adding something like 'X-GNOME-Autostart-Delay=30' to the startup file.
3. No, unless there are major problems, as outlined above.
4. Not me.

---

