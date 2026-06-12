---
title: "Live Ubuntu 9.04 not gving my right resolution in display"
date: 2009-05-26
forum: General Help
---

### Post by roshanjose on 2009-05-26
Hey can anyone help me get me get the right resolution for my monitor LG Studioworks 552V. I dont get any resolution higher than 832x624(4:3) 75Hz

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
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
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

---

### Post by KhurramM on 2009-05-26
u seem to be a unix guy, have u tried xrandr?

---

### Post by CatKiller on 2009-05-26
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

According to a driver I downloaded from the Internet, the values that you want are

```
        HorizSync       30-54
        VertRefresh     50-120
```

---

### Post by roshanjose on 2009-05-27
is that all CATKILLER..

will it work

---

### Post by CatKiller on 2009-05-27
> **roshanjose said:**
> will it work

It normally works. You'll need to restart X for it to take effect, and running it from the live cd rather than installing means that you'll have to do it every time.

---

### Post by roshanjose on 2009-06-02
i'll try that out...thanks

---

### Post by roshanjose on 2009-06-04
I made the changes in the xorg.conf as:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-54
        VertRefresh     50-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection






Now i get 800x600 which fits my monitor correctly, but the icons look bigger. Maybe 1024x768 may work  out. I'll give some outputs:

roshan@roshan:~$ xrandr
Screen 0: minimum 320 x 200, current 800 x 600, maximum 832 x 832
VGA connected 800x600+0+0 (normal left inverted right x axis y axis) 260mm x 195mm
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3*    56.2  
   640x480        85.0     75.0     72.8     75.0     66.7     59.9  
   720x400        70.1  


I tried to add 1024x768 with no success. Someone suggested me to get a graphic card. Is there any solution to this problem

---

