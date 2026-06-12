---
title: "New to Linux Xorg woes"
date: 2012-02-17
forum: Desktop Environments
---

### Post by ally_uk on 2012-02-17
Hi guys I am trying to get Compiz setup and running but being new to Linux I need some help firstly here is my xorg config.

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

The 

results of lSPCI | grep VGA

01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev 

How can I tell what version of Nvidia driver are running?

---

### Post by ally_uk on 2012-02-17
Updated the Xorg 

Section "Device"
    Identifier "Device0"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    BusID "PCI:01:00:0"
    Option "NoLogo" "true"
    Option "UseEDID" "true"
    Option "ConnectedMonitor" "DFP"
EndSection
 
Section "Files"
    ModulePath      "/usr/lib/<path to nvidia driver>"
    ModulePath      "/usr/lib/xorg/modules"
EndSection

is there a command which tells me what version of nivdia driver I'm running? my resolutions still seem to be quite low

---

