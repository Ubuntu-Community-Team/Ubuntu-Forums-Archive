---
title: "[SOLVED] Dual Monitors and Desktop Effects"
date: 2008-04-08
forum: Desktop Effects &amp; Customization
---

### Post by mistakenkindness on 2008-04-08
I am a fairly new user of Ubuntu and linux.  I am currently running 2 1680X1050 widescreen monitors.  I have a Nvidia GeForce 7600GT. 

I am able to use both monitors using xinerama, the problem is I am unable to use desktop effects.  When I attempt to enable desktop effects I get an error telling me that Deskttop effects could not be enabled.  Its getting pretty frustrating and I figured I would turn here for help.  I am including my xconf.  Any help is appreciated.

Thanks
Brad

---

### Post by tamoneya on 2008-04-08
i find that twinview works better when it comes to desktop effects.  I have twinview enabled on my setup and it handles it pretty well considering the fact that one monitor is 17" standard and the other is 22" wide.

---

### Post by mistakenkindness on 2008-04-08
> **tamoneya said:**
> i find that twinview works better when it comes to desktop effects.  I have twinview enabled on my setup and it handles it pretty well considering the fact that one monitor is 17" standard and the other is 22" wide.

When I attempt to change to twinview I get this error,  "The XRandR X extension was not found.  This extension must be supported by the X server and enabled for display configuration settings to be dynamically applicable."

---

### Post by tamoneya on 2008-04-08
try ```
sudo apt-get install xrandr
``` and then enable twinview

---

### Post by mistakenkindness on 2008-04-09
I was able to install xrandr and enable Twinview.   but I am still not able to use Desktop effects.  I still get the error: Desktop effects could not be enabled.
I have included my updated xorg.conf as well as the output from lspci.  Any help is appreciated.


```
$lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
05:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```

---

### Post by mistakenkindness on 2008-04-09
bump

---

### Post by mistakenkindness on 2008-04-10
Well after tinkering around i have it all working perfectly!!!

i used envy to install the drivers.  rebooted and it worked dont know how but it did!!!

---

