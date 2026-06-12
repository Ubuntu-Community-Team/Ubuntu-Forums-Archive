---
title: "Catalyst Control Center Won't Open"
date: 2010-05-24
forum: Desktop Environments
---

### Post by Kabraxis on 2010-05-24
Hi,
ATI Catalyst Control Center won't open, neither as Administrator.
When i try to start it from terminal, i got this error:

> Parse error on line 2 of section ServerLayout in file /etc/X11/xorg.conf
	"Identifier" is not a valid keyword in this section.
Parse error on line 2 of section ServerLayout in file /etc/X11/xorg.conf
	"Identifier" is not a valid keyword in this section.

Any suggestions?

(I'm using native, latest, so called "Ubuntu Tested" fglrx driver, and have Ati Mobility Radeon x2400HD)

---

### Post by mhgsys on 2010-05-24
post /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Kabraxis on 2010-05-24
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by mhgsys on 2010-05-24
Looks ok, At first I thought it might be a typo somewhere; 
Anyway: How did you generate that xorg.conf?

Did the ati install do that automatically?

---

### Post by Kabraxis on 2010-05-24
I didn't generated anything, just installed drivers, and i think it do the magic.

---

### Post by daemon3 on 2010-05-24
Same here...I have an ATI Radeon HD 3100.  I keep checking Synaptic and it says that amdcccle is installed.  However, when I search for amdcccle, I only see documentation, *.desktop files, and *.qm files (e.g. /usr/share/ati/amdcccle/amdcccle_th.qm).

---

### Post by mhgsys on 2010-05-24
> **Kabraxis said:**
> I didn't generated anything, just installed drivers, and i think it do the magic.

How did you install this driver?

Manually?
Or by System>Administration>Hardware drivers.?

---

### Post by tayfund on 2010-07-29
I have the same problem too. I try to start amdcccle from command line and it gives the same error.

Parse error on line 3 of section Screen in file xorg.conf
	"Identifier" is not a valid keyword in this section.
Parse error on line 3 of section Screen in file xorg.conf
	"Identifier" is not a valid keyword in this section.


My xorg.conf

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection
```

And line 3 is 
Identifier	"Default Screen"

This file is created during the installation of the ati driver by the Hardware Drivers section.

When I try to this command

aticonfig --initial --input=/etc/X11/xorg.conf

to create new xorg.conf then it gives this error;

Found fglrx primary device section
Unable to find any supported Screen sections

Is there anyone to be able to help?
Is there any idea?

---

### Post by alexshr on 2010-07-29
My friend had the exact same problem, and the re-installation of the driver for ATI (one with .run as I remember), which he had downloaded solved the problem.

Try re-installing the driver for ATI, that will automatically re-configure the Xorg.

alexshr

---

### Post by tayfund on 2010-07-29
I found another way to run amdcccle:

```
env LANG="en_US.UTF-8" amdcccle
```

You can use this with sudo. My xubuntu is in Turkish language and this is a language problem.

But still ```
env LANG="en_US.UTF-8" aticonfig --initial --input=/etc/X11/xorg.conf
``` command gives the same error.

I will try to alexshr's recommendation. Thanks.

---

### Post by tayfund on 2010-07-29
OK. I found the way to run aticonfig. First I have changed the xorg.conf with below:

```
Section "ServerLayout"
	Identifier "Builtin Default Layout"
	Screen "Builtin Default ati Screen 0"
EndSection

Section "Files"
EndSection

Section "Module"
	Load "glx"
EndSection

Section "Monitor"
	Identifier "Builtin Default Monitor"
EndSection

Section "Device"
	Identifier "Builtin Default ati Device 0"
	Driver "fglrx"
EndSection

Section "Screen"
	Identifier "Builtin Default ati Screen 0"
	Device "Builtin Default ati Device 0"
	Monitor "Builtin Default Monitor"
	DefaultDepth	24
EndSection


```

Then I run the ```
sudo aticonfig --initial --input=/etc/X11/xorg.conf
```

It works!

---

### Post by ravisghosh on 2010-08-22
> **tayfund said:**
> OK. I found the way to run aticonfig. First I have changed the xorg.conf with below:

```
Section "ServerLayout"
	Identifier "Builtin Default Layout"
	Screen "Builtin Default ati Screen 0"
EndSection

Section "Files"
EndSection

Section "Module"
	Load "glx"
EndSection

Section "Monitor"
	Identifier "Builtin Default Monitor"
EndSection

Section "Device"
	Identifier "Builtin Default ati Device 0"
	Driver "fglrx"
EndSection

Section "Screen"
	Identifier "Builtin Default ati Screen 0"
	Device "Builtin Default ati Device 0"
	Monitor "Builtin Default Monitor"
	DefaultDepth	24
EndSection


```

Then I run the ```
sudo aticonfig --initial --input=/etc/X11/xorg.conf
```

It works!

Doing this gives me the following:

```
shantanu@GreenHead:~$ sudo aticonfig --initial --input=/etc/X11/xorg.conf
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1

```

And nothing after that..

---

