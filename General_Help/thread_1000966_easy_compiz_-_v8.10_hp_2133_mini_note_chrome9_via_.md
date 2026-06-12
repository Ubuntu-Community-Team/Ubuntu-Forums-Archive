---
title: "easy compiz - v8.10 hp 2133 mini note chrome9 via chrome"
date: 2008-12-03
forum: General Help
---

### Post by luvit on 2008-12-03
easy compiz - v 8.10 intrepid ibex hp 2133 mini note chrome9 via chrome

**read all steps before proceeding**

[LIST]
[*]install 8.10 with _**[[COLOR=Blue]this method & ho 2133 BIOS rev[/COLOR]]("http://www.hp2133guide.com/forums/viewtopic.php?t=1089")**_
[LIST]
[*]if you already have a successful in stall then move to the next steps
[*][B][COLOR=Blue]
[/COLOR][/B]
[/LIST]
 
[*]System > Administration > Synaptic Package Manager
[LIST]
[*]install: **compiz-settings-manager**
[*]after installed you will find it under System > Preferences > CompizConfig Setings Manager
[*]compiz will work after the folowing steps
[URL="ftp://ftp.mangohabanero.com/public/ubuntu8.10-hp2133-compiz-info-2DEC2008/5.74.33.85a-44597.tar.gz"]
[/URL]
[/LIST]
 
[*][_[COLOR=Blue]**downlaod and install this driver**[/COLOR]_ ]("http://hp-umpc.com/luvit/Mini_Note_2133/ubuntu8.10-hp2133-compiz-info-2DEC2008/5.74.33.85a-44597.tar.gz")fom December 2nd, 2008
[LIST]
[*]follow the [[COLOR=Blue]**_readme file !!_**[/COLOR] ]("http://hp-umpc.com/luvit/Mini_Note_2133/ubuntu8.10-hp2133-compiz-info-2DEC2008/Readme.txt")(included with driver)
[/LIST]
 
[*]here is a copy of my xorg.config made for 1280x768
[LIST]
[*]**you will need to modify for your 2133 if you only support 1024x600 !!**
[*]link to my** [_[COLOR=Blue]xorg.conf[/COLOR]_]("http://hp-umpc.com/luvit/Mini_Note_2133/ubuntu8.10-hp2133-compiz-info-2DEC2008/xorg.conf")**
[/LIST]
 
[/LIST]

---

### Post by Nonsense on 2008-12-08
Could you please post a version that supports 1024x600?

I'm having difficulties setting up the VIA-driver (and Vesa) on my 8.10.

---

### Post by luvit on 2008-12-08
it's gonna take me a quite a few days. i broke my hard drive cable i am ordering a new one today.

---

### Post by Nonsense on 2008-12-08
Ok. Sorry to hear that.

I'm not sure about my modell number.

Could this be it?
FU345EA#AK8

I says on the HP-page (in Swedish) that this modell uses the following chips:
VN896NB
8237S SB

[http://h10010.www1.hp.com/wwpc/se/sv/sm/WF06b/321957-321957-64295-306995-306995-3687084-3793153.html](http://h10010.www1.hp.com/wwpc/se/sv/sm/WF06b/321957-321957-64295-306995-306995-3687084-3793153.html)

---

### Post by luvit on 2008-12-09
i'm only familiar with model numbers that look like this.

[LIST]
[*][HP 2133 Mini-note PC KX870AT ]("http://www.hp2133guide.com/hp-2133-mini-note-pc-kx870at/")
[*][HP 2133 Mini-note PC KX871AA]("http://www.hp2133guide.com/hp-2133-mini-note-pc-kx871aa/")
[*][HP 2133 Mini-note PC KX869AT]("http://www.hp2133guide.com/hp-2133-mini-note-pc-kx869at/")
[*][HP 2133 Mini-note PC KX868AT]("http://www.hp2133guide.com/hp-2133-mini-note-pc-kx868at/")
[*][HP 2133 Mini-note PC KR922UT]("http://www.hp2133guide.com/hp-2133-mini-note-pc-kr922ut/")
[/LIST]
until i get my laptop repaired, you may find useful information [[COLOR=Blue]**here**[/COLOR]]("http://www.hp2133guide.com/forums/viewtopic.php?t=1136") about enabling compiz.

---

### Post by Nonsense on 2008-12-09
Mine resembles the KX870AT except for the 6-cell battery

My spec:

1,Ghz, 2GB Ram, 120GB HD, 1024x600 resolution, BT, 3-cell battery, Vista Home Basic

---

### Post by Nonsense on 2008-12-09
Solved it.

[Here's how I did it]("http://ubuntuforums.org/showpost.php?p=6336295&postcount=15").

---

### Post by Forlong on 2008-12-09
luvit, could you please post your output of Compiz-Check: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

Thanks in advance!

---

### Post by luvit on 2008-12-09
> **Forlong said:**
> luvit, could you please post your output of Compiz-Check: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

Thanks in advance!

i should have my mini note back by firday or saturday. :)

---

### Post by windowsseven on 2008-12-11
I've set up a site for us with Hp 2133, [http://www.ubuntu2133.blogspot.com/]("http://www.ubuntu2133.blogspot.com/")

Will exist Installation guides, driver installations, compiz and many more useful tutorials!

Can i please get permission to publish this guide and give credits to you "luvit"??


It's inspired by the ubuntu1501.com blog!

---

### Post by luvit on 2008-12-12
> **windowsseven said:**
> Can i please get permission to publish this guide and give credits to you "luvit"??

sure, please use this link as your source: _**[http://www.hp2133guide.com/forums/viewtopic.php?t=1136](http://www.hp2133guide.com/forums/viewtopic.php?t=1136)**_
thanks, windowsseven!

---

### Post by daniromen on 2009-01-16
thanks for your xorg file luvit, but in mi hp does not work ok, here is my modified file that works so fine.
```
Section "ServerFlags"
#	Option		"DefaultServerLayout"	"LCD-clone"
#	Option		"DefaultServerLayout"	"CRT-clone"
#	Option		"DefaultServerLayout"	"LCD-only"
#	Option		"DefaultServerLayout"	"CRT-only"

	Option		"AllowMouseOpenFail"	"on"
	Option		"Pixmap"		"32"
    EndSection

# Default locations of font files - change if required.

    Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

	ModulePath	"/usr/lib/xorg/modules"
	InputDevices	"/dev/gpmdata"
	InputDevices	"/dev/input/mice"
    EndSection

    Section "DRI"
	Group 0
	Mode 0666
    EndSection

    Section "InputDevice"
	Identifier	"Keyboard 0"
	Driver		"kbd"
	Option		"Protocol"        "Standard"
	Option		"XkbLayout"       "us"
	Option		"XkbModel"        "pc104"
	Option		"XkbRules"        "xfree86"
    EndSection

    Section "InputDevice"
	Identifier	"Mouse 0"
	Driver		"synaptics"
	Option		"Buttons"         "5"
	Option		"Device"          "/dev/input/mice"
	Option		"Emulate3Buttons" "on"
	Option		"InputFashion"    "Mouse"
	Option		"Name"            "Synaptics Touchpad"
	Option		"Protocol"        "explorerps/2"
	Option		"SHMConfig"       "on"  # GUI setting access
	Option		"ZAxisMapping"    "4 5"
    EndSection

    Section "InputDevice"
	Identifier	"Mouse 1"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Buttons"         "5"
	Option		"Device"          "/dev/input/mice"
	Option		"Emulate3Buttons" "on"
	Option		"Name"            "Generic Mouse"
	Option		"Protocol"        "Auto"
	Option		"Vendor"          "Sysp"
	Option		"ZAxisMapping"    "4 5"
    EndSection

    Section "Module"
	Load  "glx"
	Load  "dri"
	Load  "extmod"
	Load	"dbe"
	Load	"freetype"
	Load	"record"
	Load	"v4l"
    EndSection

# Device outputs not connected in the HP-2133

    Section "Monitor"
	Identifier "Monitor"
	ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
	ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
	ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
	ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
	ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
	ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync
	ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync
	ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
	ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync
	ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync
	ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync
	ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync
	ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
	ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
	ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
	ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
	ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
	ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync
	ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync
	ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync
	ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync
	ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
	ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync
	ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
	ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
	ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
	ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
	ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
	ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
	ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
	ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
	ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
	ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
	Option		"Ignore"	"true"
    EndSection

    Section "Monitor"
	Identifier "Monitor"
	ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
	ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
	ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
	ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
	ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
	ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync
	ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync
	ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
	ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync
	ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync
	ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync
	ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync
	ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
	ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
	ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
	ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
	ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
	ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync
	ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync
	ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync
	ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync
	ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
	ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync
	ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
	ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
	ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
	ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
	ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
	ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
	ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
	ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
	ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
	ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
	Option		"Ignore"	"true"
    EndSection

# Internal LCD does not return DDC information.
# Define first channel:

    Section "Modes"	# See also "HP-2133 Known Modes" at file end.
	Identifier	"HP-2133 LCD Modes"
	# Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
	Modeline "1280x768-60.0"   80.14  1280 1344 1480 1680  768 769 772 795
	# Default mode "1280x720": 74.6 MHz, 44.2 kHz, 59.2 Hz
	# Modeline "1280x720-59.2"   74.60  1280 1341 1474 1688  720 721 724 746 -hsync +vsync
	# Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
	#Modeline "1024x768-60.0"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
    EndSection

    Section "Monitor"
	Identifier "Monitor"
	ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
	ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
	ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
	ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
	ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
	ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync
	ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync
	ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
	ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync
	ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync
	ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync
	ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync
	ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
	ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
	ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
	ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
	ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
	ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync
	ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync
	ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync
	ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync
	ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
	ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync
	ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
	ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
	ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
	ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
	ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
	ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
	ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
	ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
	ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
	ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
	VertRefresh	50.00-100.00            # X11 discovery claim
	HorizSync	30.00-113.00            # X11 discovery claim
	# Dot clock range: 20.00-270.00MHz      # X11 discovery claim
	# Typical dot pitch is: .1515mm x .1515mm
	# Native resolution is: 1280x768
	DisplaySize	193 116                 # Actual: 193.9 116.4
	UseModes	"HP-2133 LCD Modes"
	Option		"PreferredMode"		"1280x768-60.0"
	Option		"DPMS"
    EndSection

    Section "Device"
	Driver "via"
	VendorName  "VIA Tech"
	BoardName   "via"
	        #Option "PanelID" "0"    #640x480,    Single,    Dithering
	Identifier	"via-P4M900 Device 0"
	BusID		"PCI:1:0:0"
	Option		"Monitor-LCD"		"HP-2133 LCD"
	Option		"PanelID"		"3"	# 1280x720 Single, Dithering
#	Option		"PanelID"       	"12"    # 1280x768 Single, Non-Dithering
	Option		"NoDDCValue"
    EndSection

    Section "Screen"
	Monitor  "Monitor"
	SubSection "Display"
		Modes  "1280x768" 
		Virtual 1280 768
		Depth  24
	EndSubSection
	Identifier	"via-P4M900 Screen 0"
	Device		"via-P4M900 Device 0"
	Subsection	"Display"
	    Depth	24 			# Depth 16 broke
#	    Modes	"1280x768-60.0" "1280x720-59.2" "1024x768-60.0"
            Modes	"1280x768-60.0"
#	    Virtual	1280 768
	EndSubsection
	# Device section options:
	Option		"ForceLCD"		"true"	# BIOS setting over-ride
	Option		"ActiveDevice"		"LCD"
	Option		"VideoOnDevice"		"LCD"	# Broke ?
	Option		"SetMpegFBNumber"	"true"	# Unknown if required
    EndSection

# External device expected to return DDC information.
# Flying on full auto here, the smoke you smell may be your monitor:

    Section "Monitor"
	Identifier "Monitor"
	ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
	ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
	ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
	ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
	ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
	ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync
	ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync
	ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
	ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync
	ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync
	ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync
	ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync
	ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
	ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
	ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
	ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
	ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
	ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync
	ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync
	ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync
	ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync
	ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
	ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync
	ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
	ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
	ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
	ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
	ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
	ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
	ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
	ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
	ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
	ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
	Option		"DPMS"
    EndSection

    Section "Device"
	Driver "via"
	VendorName  "VIA Tech"
	BoardName   "via"
	        #Option "PanelID" "0"    #640x480,    Single,    Dithering
	Identifier	"via-P4M900 Device 1"
	BusID		"PCI:1:0:0"
	Option		"Monitor-CRT"		"HP-2133 External"
    EndSection

    Section "Screen"
	Monitor  "Monitor"
	SubSection "Display"
		Modes  "11280x768" 
		Virtual 1280 768
		Depth  24
	EndSubSection
	Identifier	"via-P4M900 Screen 1"
	Device		"via-P4M900 Device 1"
	Subsection	"Display"
	    Depth	24 			# Depth 16 broke
#	    Virtual	2048 1536
	EndSubsection
	# Device section options:
	Option		"ActiveDevice"		"CRT"
	Option		"VideoOnDevice"		"CRT"	# Broke ?
	Option		"SetMpegFBNumber"	"true"	# Unknown if required
    EndSection

# Single channel, dual outputs driven, screen descriptions

    Section "Screen"
	Monitor  "Monitor"
	SubSection "Display"
		Modes  "1280x768" 
		Virtual 1280 768
		Depth  24
	EndSubSection
	Identifier	"via-P4M900 Clone 0"
	Device		"via-P4M900 Device 0"
	Subsection	"Display"
	    Depth	24			# Depth 16 broke
#	    Modes	"1280x768" "1200x720" "1024x768"
            Modes	"1280x768"
#	    Virtual	2048 1536
	EndSubsection
	# Device section options:
	Option		"ActiveDevice"		"LCD,CRT"
	Option		"ForceLCD"		"true"
	Option		"VideoOnDevice"		"LCD"	# Broke ?
	# Option true turned off mouse on LCD:
	Option		"Simultaneous"		"false"
    EndSection

    Section "Screen"
	Monitor  "Monitor"
	SubSection "Display"
		Modes  "1280x768" 
		Virtual 1280 768
		Depth  24
	EndSubSection
	Identifier	"via-P4M900 Clone 1"
	Device		"via-P4M900 Device 1"
	Subsection	"Display"
	    Depth	24 			# Depth 16 broke
#	    Virtual	2048 1536
	EndSubsection
	# Device section options:
	Option		"ActiveDevice"		"CRT,LCD"
	Option		"ForceLCD"		"true"
	Option		"VideoOnDevice"		"CRT"	# Broke ?
	# Option true turned off mouse on LCD:
	Option		"Simultaneous"		"false"
    EndSection

# RandR is broken, in various places, for various reasons:
# The driver does not recognize the RandR naming conventions:
# (WW) VIA(0): Option "Monitor-LCD" is not used
# (WW) VIA(0): Option "Monitor-CRT" is not used
# (WW) VIA(0): Option "Monitor-DVI" is not used
# (WW) VIA(0): Option "Monitor-TV" is not used
# (==) RandR enabled
# And if you can't name them, xrandr can't select them.  Bummer.

# Old-school layouts

    Section "ServerLayout"
	Option "RandR" "False"
	Identifier	"LCD-clone"
	InputDevice	"Keyboard 0"	"CoreKeyBoard"
	InputDevice	"Mouse 0"	"SendCoreEvents"
	InputDevice	"Mouse 1"	"SendCoreEvents"
	Screen		"via-P4M900 Clone 0"
    EndSection

    Section "ServerLayout"
	Option "RandR" "False"
	Identifier	"CRT-clone"
	InputDevice	"Keyboard 0"	"CoreKeyBoard"
	InputDevice	"Mouse 0"	"SendCoreEvents"
	InputDevice	"Mouse 1"	"SendCoreEvents"
	Screen		"via-P4M900 Clone 1"
    EndSection

    Section "ServerLayout"
	Option "RandR" "False"
	Identifier	"LCD-only"
	InputDevice	"Keyboard 0"	"CoreKeyBoard"
	InputDevice	"Mouse 0"	"SendCoreEvents"
	InputDevice	"Mouse 1"	"SendCoreEvents"
	Screen		"via-P4M900 Screen 0"
    EndSection

    Section "ServerLayout"
	Option "RandR" "False"
	Identifier	"CRT-only"
	InputDevice	"Keyboard 0"	"CoreKeyBoard"
	InputDevice	"Mouse 0"	"SendCoreEvents"
	InputDevice	"Mouse 1"	"SendCoreEvents"
	Screen		"via-P4M900 Screen 1"
    EndSection

Section "Modes"
    Identifier  "HP-2133 Known Modes"
    ## X11 discovered modes are marked "Default mode";
    ## VIA reference file modes are marked "Extra mode" in this list.
    ## All have been renamed to include refresh rate and not conflict
    ## with the standard VESA names (most are VESA standard rates).

    ## Refresh rate 60Hz - The prefered LCD refresh rate.

    # Default mode "2048x1536": 266.9 MHz, 95.3 kHz, 60.0 Hz
    Modeline "2048x1536-60.0"  266.95  2048 2200 2424 2800  1536 1537 1540 1589 -hsync +vsync
    # Default mode "1920x1440": 234.0 MHz, 90.0 kHz, 60.0 Hz
    Modeline "1920x1440-60.0"  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync
    # Default mode "1920x1200": 193.2 MHz, 74.5 kHz, 60.0 Hz
    Modeline "1920x1200-60.0"  193.16  1920 2048 2256 2592  1200 1201 1204 1242

    ## 1080p (image 16:9, pixel 1:1)
    # Default mode "1920x1080": 172.9 MHz, 67.1 kHz, 60.0 Hz
    Modeline "1920x1080-60.0"  172.90  1920 2043 2249 2578  1080 1081 1084 1118 -hsync +vsync

    # Default mode "1856x1392": 218.3 MHz, 86.4 kHz, 60.0 Hz
    Modeline "1856x1392-60.0"  218.30  1856 1952 2176 2528  1392 1393 1396 1439 -hsync +vsync
    # Default mode "1856x1392": 218.6 MHz, 86.5 kHz, 60.0 Hz
    Modeline "1856x1392-60.0"  218.57  1856 1992 2192 2528  1392 1393 1396 1441 -hsync +vsync
    # Default mode "1792x1344": 204.8 MHz, 83.7 kHz, 60.0 Hz
    Modeline "1792x1344-60.0"  204.80  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync
    # Default mode "1792x1344": 203.0 MHz, 83.5 kHz, 60.0 Hz
    Modeline "1792x1344-60.0"  202.97  1792 1920 2112 2432  1344 1345 1348 1391 -hsync +vsync
    # Default mode "1680x1050": 147.1 MHz, 65.2 kHz, 60.0 Hz
    Modeline "1680x1050-60.0"  147.14  1680 1784 1968 2256  1050 1051 1054 1087
    # Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
    Modeline "1600x1200-60.0"  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
    # Default mode "1600x1024": 136.4 MHz, 63.6 kHz, 60.0 Hz
    Modeline "1600x1024-60.0"  136.36  1600 1704 1872 2144  1024 1025 1028 1060 -hsync +vsync
    # Default mode "1600x900": 119.0 MHz, 55.9 kHz, 60.0 Hz
    Modeline "1600x900-60.0"  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync
    # Default mode "1440x1050": 126.2 MHz, 65.2 kHz, 60.0 Hz
    Modeline "1440x1050-60.0"  126.20  1440 1536 1688 1936  1050 1051 1054 1087 -hsync +vsync
    # Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
    Modeline "1440x900-60.2"  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync
    # Default mode "1440x900": 106.5 MHz, 55.9 kHz, 60.0 Hz
    Modeline "1440x900-60.0"  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync
    # Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
    Modeline "1400x1050-60.0"  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync

    ## Alternate version of 720p (image approx 16:9, pixel 1:1)
    # Default mode "1366x768": 85.9 MHz, 47.7 kHz, 60.0 Hz
    Modeline "1366x768-60.0"   85.86  1366 1440 1584 1800  768 769 772 795 -hsync +vsync

    # Default mode "1360x768": 85.5 MHz, 49.0 kHz, 60.7 Hz
    Modeline "1360x768-60.7"   85.50  1360 1392 1712 1744  768 783 791 807 +hsync +vsync
    # Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
    Modeline "1280x1024-60.0"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
    # Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
    Modeline "1280x960-60.0"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
    # Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
    Modeline "1280x800-60.0"   83.46  1280 1344 1480 1680  800 801 804 828
    # Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
    Modeline "1280x768-60.0"   80.14  1280 1344 1480 1680  768 769 772 795

    ## One version of 720p (image 16:9, pixel 1:1)
    # Default mode "1280x720": 74.6 MHz, 44.2 kHz, 59.2 Hz
    Modeline "1280x720-59.2"   74.60  1280 1341 1474 1688  720 721 724 746 -hsync +vsync

    # Default mode "1280x600": 61.5 MHz, 37.3 kHz, 60.0 Hz
    Modeline "1280x600-60.0"   61.50  1280 1336 1464 1648  600 601 604 622 -hsync +vsync
    # Default mode "1200x720": 70.2 MHz, 44.8 kHz, 60.0 Hz
    Modeline "1200x720-60.0"   70.18  1200 1256 1384 1568  720 721 724 746 -hsync +vsync
    # Default mode "1152x720": 67.3 MHz, 44.8 kHz, 60.0 Hz
    Modeline "1152x720-60.0"   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync
    # Default mode "1088x612": 53.0 MHz, 38.0 kHz, 60.0 Hz
    Modeline "1088x612-60.0"   52.95  1088 1128 1240 1392  612 613 616 634 -hsync +vsync
    # Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
    Modeline "1024x768-60.0"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
    # Default mode "1024x600": 49.0 MHz, 37.3 kHz, 60.0 Hz
    Modeline "1024x600-60.0"   48.96  1024 1064 1168 1312  600 601 604 622 -hsync +vsync
    # Default mode "1024x512": 41.3 MHz, 31.9 kHz, 60.0 Hz
    Modeline "1024x512-60.0"   41.30  1024 1056 1160 1296  512 513 516 531 -hsync +vsync
    # Default mode "1000x600": 48.1 MHz, 37.3 kHz, 60.0 Hz
    Modeline "1000x600-60.0"   48.07  1000 1040 1144 1288  600 601 604 622 -hsync +vsync
    # Default mode "960x600": 46.0 MHz, 37.3 kHz, 60.0 Hz
    Modeline "960x600-60.0"   45.98  960 1000 1096 1232  600 601 604 622 -hsync +vsync
    # Default mode "856x480": 31.7 MHz, 29.8 kHz, 59.9 Hz
    Modeline "856x480-59.9"   31.70  856 872 960 1064  480 481 484 497 -hsync +vsync
    # Default mode "848x480": 31.5 MHz, 29.8 kHz, 60.0 Hz
    Modeline "848x480-60.0"   31.50  848 864 952 1056  480 481 484 497 -hsync +vsync
    # Extra mode
    ModeLine "800x480-x" 29.58 800 816 896 992 480 481 484 497
    # Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
    Modeline "800x600-60.3"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
    # Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
    Modeline "800x600-56.2"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
    # Default mode "800x480": 40.0 MHz, 37.9 kHz, 60.3 Hz
    Modeline "800x480-60.3"   40.00  800 832 960 1056  480 541 545 628 -hsync +vsync
    # Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
    Modeline "720x576-60.1"   32.70  720 744 816 912  576 577 580 597 -hsync +vsync

    ## NTSC-M  (actually 710.9x486 active area)
    # Default mode "720x480": 26.7 MHz, 29.8 kHz, 60.0 Hz
    Modeline "720x480-60.0"   26.70  720 736 808 896  480 481 484 497 -hsync +vsync

    # Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
    Modeline "640x480-59.9"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
    # Default mode "480x640": 24.8 MHz, 39.8 kHz, 60.0 Hz
    Modeline "480x640-60.0"   24.82  480 504 552 624  640 641 644 663 -hsync +vsync

    ## Refresh rate 65Hz

    # Default mode "1600x1200": 175.5 MHz, 81.2 kHz, 65.0 Hz
    Modeline "1600x1200-65.0"  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync

    ## Refresh rate 70Hz

    # Default mode "1600x1200": 189.0 MHz, 87.5 kHz, 70.0 Hz
    Modeline "1600x1200-70.0"  189.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
    # Default mode "1400x1050": 151.0 MHz, 77.0 kHz, 70.0 Hz
    Modeline "1400x1050-70.0"  151.00  1400 1464 1656 1960  1050 1051 1054 1100 +hsync +vsync
    # Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
    Modeline "1024x768-70.1"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync

    ## Refresh rate 72Hz

    # Default mode "1920x1200": 230.0 MHz, 91.0 kHz, 72.8 Hz
    Modeline "1920x1200-72.8"  230.00  1920 1936 2096 2528  1200 1201 1204 1250 -hsync -vsync
    # Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
    Modeline "800x600-72.2"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
    # Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
    Modeline "640x480-72.8"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync

    ## Refresh Rate 75Hz

    # Default mode "1792x1344": 261.0 MHz, 106.3 kHz, 75.0 Hz
    Modeline "1792x1344-75.0"  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync
    # Default mode "1600x1200": 202.5 MHz, 93.8 kHz, 75.0 Hz
    Modeline "1600x1200-75.0"  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
    # Extra mode "1440x1050"
    ModeLine "1440x1050-x" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
    # Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
    Modeline "1400x1050-74.8"  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync
    # Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
    Modeline "1280x1024-75.0"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
    # Extra mode "1280x768"
    ModeLine "1280x768-x" 103.0 1280 1360 1496 1712 768 769 772 802
    # Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
    Modeline "1152x864-75.0"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
    # Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
    Modeline "1024x768-75.0"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
    # Extra mode "1024x512"
    ModeLine "1024x512-x" 53.3 1024 1072 1176 1328 512 513 516 535
    # Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
    Modeline "800x600-75.0"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
    # Extra mode "856x480"
    ModeLine "856x480-x" 41.3 856 888 976 1096 480 481 484 502
    # Extra mode "848x480"
    ModeLine "848x480-x" 41.0 848 880 968 1088 480 481 484 502
    # Extra mode "720x576"
    ModeLine "720x576-x" 42.6 720 760 832 944 576 577 580 602
    # Extra mode "720x480"
    ModeLine "720x480-x" 34.9 720 752 824 928 480 481 484 502
    # Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
    Modeline "640x480-75.0"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync

    ## Refresh rate 85Hz

    # Default mode "1600x1200": 229.5 MHz, 106.2 kHz, 85.0 Hz
    Modeline "1600x1200-85.0"  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
    # Default mode "1400x1050": 184.0 MHz, 93.9 kHz, 85.3 Hz
    Modeline "1400x1050-85.3"  184.00  1400 1464 1656 1960  1050 1051 1054 1100 +hsync +vsync
    # Extra mode "1440x1050"
    ModeLine "1440x1050-x" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
    # Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
    Modeline "1280x1024-85.0"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync
    # Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
    Modeline "1280x960-85.0"  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync
    # Extra mode "1280x768"
    ModeLine "1280x768-x" 118.5 1280 1368 1504 1728 768 769 772 807
    # Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
    Modeline "1152x864-85.1"  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync
    # Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
    Modeline "1024x768-85.0"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
    # Extra mode "848x480"
    ModeLine "848x480-x" 47.4 848 888 976 1104 480 481 484 505
    # Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
    Modeline "800x600-85.1"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
    # Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
    Modeline "640x480-85.0"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
EndSection
```

i have a hp 2133 (1GB ram, 120Gb, 1.6Ghz, it came with vista business)

---

### Post by linuxoholic on 2009-02-24
hello Dani,
Thanks a lot for sharing your xorg.conf modified file; in fact this file solved my problem of making the external display work, yet it gave me wrong resolution on my internal hp-2133 lcd

I have a hp-mini with the same specs as you do, except that it's lcd is the smaller version (1024x600)

attached is my currently installed xorg.conf file (shows perfectly on the internal LCD - External Display NOT WORKING).

I'm not that expert in X settings, so could you please have a look at this file, and advise me with what should be modified in your file to match my situation, so that I could have both internal and external displays working.

Many thanks!

> 
# xorg.conf (X.Org X Window System server configuration file)

#

# This file was based on one generated by dexconf.

# Lots of testing was done by Jonathan Austin (Who) 

# Thanks to mikez's docs and examples for teaching me!

# Bits of the Suse Xorg.conf were used too.

#

# This is very much a work in progress. I accept no responsibility

# for any damage to you, your hardware, or your mental state that

# this configuration file may cause. Provided As Is, like Ubuntu is



Section "ServerFlags"

        #Change the default server layout from "main" to "randry" if you want to use RandR. Compiz isn't well supported in randry

        Option          "DefaultServerLayout"   "main"



        Option          "AllowMouseOpenFail"    "on"

        Option          "Pixmap"                "32"

    EndSection





###____________________________________________________________________________/ Devices /______

Section "Device"

        Identifier      "Main Video Device"



        Driver "via"

        VendorName  "VIA Tech"

        BoardName   "via"

        

        Option "ActiveDevice" "LCD"                     #required to make the resolution correct without RandR

        Option "PanelID" "9"                           #SUSE uses this, seems not to be reqd

        Option "ReDrawColorkey" "TRUE" # testing

        #Option "DeviceSwitchHotkey"  #Kills HwCursor! How weird Possibly necessary if ActiveDevice set to LCD,CRT

        #Option "HQVManualSwitch" # No idea what this does   



EndSection



Section "Device"

        Identifier      "RandR Video Device"



        Driver "via"

        VendorName  "VIA Tech"

        BoardName   "via"



        Option "ActiveDevice" "LCD"                     #not sure of effect with randr (someone want to test this?) Setting it to LCD,CRT doesn't seem to help in getting external display work with randr. If you set LCD,CRT you need to set DeviceSwitchHotkey

        Option "PanelID" "12"                           #SUSE uses this, seems not to be reqd



        Option "UseRandR12"  # I WANT to use this (it works, almost)

        #Option "HWCursor" # Doesn't restore cursor, but it does work withOUT RandR

        Option "SWCursor" # Does restore cursor, BUT leaves distortion with Compiz      

        #Option "DeBlockingEnable" # No visible impact, doesn't fix HWCursor 

        #Option "HQVManualSwitch" # leaves SW cursor intact, no visible improvement, doesn't fix HWcursor

        Option "DeviceSwitchHotkey"  #Necessary if ActiveDevice set to LCD,CRT

EndSection



###____________________________________________________________________________/ Monitors /______



Section "Monitor"

        Identifier "Main LCD"

        #DisplaySize 250 150 # WARNING: Screws RandR

        HorizSync    28-50

        ModelName    "1024X600@60HZ"

        Option       "DPMS"

        VendorName   "HP 2133 Internal Display"

        VertRefresh  50-61

        UseModes     "2133-Modes"

EndSection



Section "Monitor"

        Identifier "RandR LCD"

        #DisplaySize 250 150 # WARNING: Screws RandR

        HorizSync    28-50

        ModelName    "1280X768@60HZ"

        Option       "DPMS"

        VendorName   "HP 2133 Internal Display"

        VertRefresh  50-61

        UseModes     "2133-Modes"

EndSection

###_____________________________________________________________________________/ Screens /______



Section "Screen"

        Identifier      "Main Screen"



        Monitor  "Main LCD"

        SubSection "Display"

                Modes  "1024x600" 

                Virtual 1024 600

                Depth  24

        EndSubSection

        Device          "Main Video Device"

        Option          "ForceLCD"              "true"

        Option          "ActiveDevice"          "LCD"

        Option          "VideoOnDevice"         "LCD"   

        Option          "SetMpegFBNumber"       "true"

        #Option         "ShadowFB"              "true" # distorts Compiz lots. Helps video with Metacity compositor

        Option          "NoDDCValue"            "on"

EndSection



Section "Screen"

        Identifier      "RandR Screen"



        Monitor  "RandR LCD"

        SubSection "Display"

                Modes  "1280x768" 

                Virtual 1280 768

                Depth  24

        EndSubSection



        Device          "RandR Video Device"

        Option          "ForceLCD"              "true" #Doesn't seem to be necessary?

        Option          "VideoOnDevice"         "LCD"   

        Option          "SetMpegFBNumber"       "true"

        Option          "NoDDCValue"            "on" #Test what this does!!

EndSection



Section "Module"

        Load  "glx"

        Load  "dri"

        Load  "extmod"

EndSection



Section "DRI"

        Group 0

        Mode 0666

EndSection



###_____________________________________________________________________/ ServerLayouts /______

Section "ServerLayout"

        Option "RandR" "False"

        Identifier "main"

        Screen "Main Screen"

EndSection



Section "ServerLayout"

        Identifier "randry"

        Screen "RandR Screen"

EndSection



###_______________________________________________________________________/ Modes /______

Section "Modes"

        Identifier "All-Modes"

        ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497

        ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597

        ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497

        ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497

        ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497

        ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync

        ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync

        ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531

        ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync

        ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync

        ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync

        ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync

        ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746

        ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795

        ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync

        ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync

        ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync

        ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087

        ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync

        ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync

        ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync

        ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync

        ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118

        ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync

        ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502

        ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602

        ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502

        ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502

        ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535

        ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802

        ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096

        ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807

        ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103

        ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505

EndSection



Section "Modes"

        Identifier "2133-Modes"

        Modeline        "1280x768" 78.80 1280 1344 1480 1680 768 769 772 795

        Modeline        "1280x768" 77.37 1280 1344 1480 1680 768 769 772 794

        Modeline        "1024x768" 63.04 1024 1080 1184 1344 768 769 772 795

        Modeline        "1024x768" 61.89 1024 1080 1184 1344 768 769 772 794

        Modeline        "1280x600" 59.79 1280 1328 1456 1632 600 601 604 621

        Modeline        "1280x600" 58.78 1280 1328 1456 1632 600 601 604 621

        Modeline        "1024x600" 48.07 1024 1064 1168 1312 600 601 604 621

        Modeline        "1024x600" 47.26 1024 1064 1168 1312 600 601 604 621

        Modeline        "800x600" 37.52 800 832 912 1024 600 601 604 621

        Modeline        "800x600" 36.88 800 832 912 1024 600 601 604 621

        Modeline        "768x576" 34.32 768 792 872 976 576 577 580 596

        Modeline        "768x576" 33.74 768 792 872 976 576 577 580 596

        Modeline        "640x480" 23.46 640 656 720 800 480 481 484 497

        Modeline        "640x480" 23.06 640 656 720 800 480 481 484 497

        Modeline        "800x600" 38.22 800 832 912 1024 600 601 604 622

EndSection



---

### Post by pthickett on 2009-02-28
The driver link doesnt work! I have found a load of links on the via website, but I have no idea what specific chipset I have! 

If anyone can help that would be awesome!

Thanks

---

### Post by luvit on 2009-03-17
> **pthickett said:**
> The driver link doesnt work! I have found a load of links on the via website, but I have no idea what specific chipset I have! 

If anyone can help that would be awesome!

Thanks
driver link has been updated... thanks.

---

### Post by j3_ on 2009-04-01
hello and thanks for the xorg.conf file, you saved my life ;)

I have a small problem with video playback. When I try to play a movie the LCD goes black and the movie only plays from the VGA port on an external monitor. I would like to either hot switch between VGA and LCD display or maybe edit the xorg.conf to disable it.

Note that whenever I run any non-commandline program I get this error:

Xlib:  extension "RANDR" missing on display ":0.0".

Thank you

---

### Post by underdarkonsole on 2009-05-11
thank's guy's i find driver for via chrome9 that can enabled compiz. And finaly my laptop can run compiz ....

[http://underdarkonsole.blogspot.com/2009/04/axio-via-chrome9-cn896-compiz-is-done.html](http://underdarkonsole.blogspot.com/2009/04/axio-via-chrome9-cn896-compiz-is-done.html)

---

