---
title: "ATI + Jaunty + desktop effects = help!"
date: 2009-06-05
forum: Desktop Environments
---

### Post by unkillbob on 2009-06-05
Hi,

I've installed the ATI drivers on jaunty using [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide) and can't get desktop effects to work!  Every time I enable desktop effects I get "Desktop effects could not be enabled".

```
$ glxinfo | grep 'direct rendering'
direct rendering: Yes
```

```
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 XT
OpenGL version string: 2.1.8664
```

```
$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV610 [Radeon HD 2400 XT]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)
```

/var/log/Xorg.0.log is riddled with:
```
(WW) AIGLX: 3D driver claims to not support visual 0x23
```

Any help will be greatly appreciated!
Thanks!

---

### Post by unkillbob on 2009-06-07
Has noone else had this problem?

---

### Post by 37fleetwood on 2009-06-07
sadly I found it was quicker, cheaper, and easier to simply go buy an Nvidia card and throw the ATI card in the bin. I guess you can get Compiz working with some of the ATI cards but they always seem to fight you.
sorry for the bad news.

---

### Post by unkillbob on 2009-06-08
Yeah my laptop and home pc both have nvidia and it just worked out of the box.  I guess I'll just have to live without the pretty at work for now :(

---

### Post by krazyd on 2009-06-08
the open source radeon driver is looking like having 3D in the next 6 months, so you don't have too long to wait.. ;)

---

### Post by braete on 2009-06-08
try the 9.5 driver from amd/ati site
i also have a 2400xt and it works as it should

---

### Post by Hund on 2009-06-08
> **krazyd said:**
> the open source radeon driver is looking like having 3D in the next 6 months, so you don't have too long to wait.. ;)

I tried the Radeon driver a few weeks ago with my ATI HD4850 card and 3D worked great, I had no problem using Compiz etc.

---

### Post by unkillbob on 2009-06-08
> **braete said:**
> try the 9.5 driver from amd/ati site
i also have a 2400xt and it works as it should

This is with the 9.5 driver.  I did however have to manually hack my xorg.conf to get dual screen going, potentially I've done something wrong?

My xorg.conf:
```

Section "Monitor"
	Identifier  "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier  "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
EndSection

Section "Extensions"
	Option     "Composite" "Enable"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen      1  "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
	Option	       "xinerama" "on"
	Option	       "clone" "off"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
	Screen      0
	Driver	"ati"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
	Screen      1
	Driver	"ati"
EndSection

Section "ServerFlags"
	Option         "DontZap" "false"
EndSection

```

---

### Post by unkillbob on 2009-06-08
> **krazyd said:**
> the open source radeon driver is looking like having 3D in the next 6 months, so you don't have too long to wait.. ;)

With the radeon driver I get:

```

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV610 [Radeon HD 2400 XT]
 Driver in use:         radeon
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

---

### Post by unkillbob on 2009-06-08
Also note that with the ati 9.5 driver, I can get compiz working with just single screen (or clone), but couldn't get it going once I'd got dual screen working.

---

### Post by unkillbob on 2009-06-10
Fixed.

Upon further inspection of my Xorg.0.log I found:
```
(WW) fglrx(0): Big Desktop related functionalities are replaced by RandR 1.2!
(WW) fglrx(0): Xorg.conf options, DesktopSetup and ScreenOverlap, of driver section are not supported when RandR 1.2 is enabled!
(WW) fglrx(0): Xorg.conf option EnableMonitor of driver section is not supported when RandR 1.2 is enabled!

```

This led me to discover [this post.]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/347758/comments/14")  Following the instructions on that post fixed my problem.

---

