---
title: "Problems with Compiz after Presentation"
date: 2009-02-01
forum: General Help
---

### Post by winding.roadie on 2009-02-01
Hey everyone,

I'm having some difficulties re-enabling Compiz after I had to give a presentation using a projector.  This happened to me before, but I was able to restart the desktop using 
```
sudo /etc/init.d/gdm restart
```
This time however, I cannot enable desktop effects even after restarting.

One of my problems could be that my card might be Blacklisted.  However, everything worked before, so I'm guessing this may not be the case.  Anyways, here's the output of my lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

I've also tried doing a reinstall of Compiz using Synaptic, but to no avail.  Any suggestions?

EDIT: Aha! I may have found the problem, but still don't have an idea for the solution.

I ran compiz-check, which previously worked fine.  This time, it gave me the following:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```

Would the rasterizer be something related to the projector?

---

### Post by Tharenth on 2009-02-02
I had exactly the same problem after my laptop was connected to an LCD TV. I hadn't discovered compiz-check back then but when trying to start compiz from terminal it said: "Software rasterizer detected, aborting".

There were also some other issues like the number of desktops had changed from 3 to 2 and a number of icons in the upper right corner were in wrong position. They used to be on the left side of the date but now they were on the right side of the switch user/shutdown button. My HPLIP icon is now loose on the desktop and any programs that I start, eg. Pidgin, don't have their icon anywhere to be seen.


At some point compiz did start again (sorry, but I didn't really documentate what I did) but now there is a new problem. When enabling normal visual effects from System -> Preferences -> Appearance, one third of the screen goes black. Check my screenshot. 

I can move the mouse to the black area but any windows can't be moved there. They just cling to the edge of the area like they would do to the borders of my usual desktop.


When compiz didn't start there was an extra "Unknown" screen to be seen at System -> Preferences -> Screen Resolution even while any external displays weren't attached. Now that compiz starts there is only one which is the screen of my laptop. 

Could this be part of the problem? Did compiz try to display its effects on the screen of the external monitor even when it was detached resulting as the rasterizer error? And now when there is only one screen it's able to start but is a bit lost after the external display?

All the visual effects were shown on the external screen at the time.


My laptop has the same Intel display controller and I'm running Ubuntu 8.10. The resolution of my display is 1280 x 800 though when the external display was in use only 1024 x 768. The external display's resolution was (something) x 768 in widescreen.

Hope this helps! Any ideas are welcome as I have no idea what to do next. I'll gladly post any additional info if needed.

---

### Post by winding.roadie on 2009-02-02
Here was my solution (thanks to Forlong)

Open your xorg.conf using the following:

```
gksu gedit /etc/X11/xorg.conf
```

There should be a bit in there that looks similar to this:

```
SubSection "Display"
		Virtual	2304 800
	EndSubSection
```

Remove that, save the file, and relogin.  Everything should be back to normal (or at least it is for me).

From now on, I'm just going to use a separate login without Compiz whenever I have to do a presentation.

---

### Post by Tharenth on 2009-02-03
There is no such thing in my xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by winding.roadie on 2009-02-03
Hmm, the only difference between my xorg.conf is the

```
Option		"UseFBDev"		"true"
```

Try removing that, and see what happens.

---

### Post by Tharenth on 2009-02-04
Commenting that line and restarting X had no effect. I also tried re-installing all compiz packages but it didn't help either.

Would there be some way to restore the default settings that the Ubuntu installer creates?

---

