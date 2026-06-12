---
title: "Triple Head probs with 2x nvidia cards"
date: 2006-06-04
forum: Desktop Environments
---

### Post by UrbanSlayer on 2006-06-04
Hi,

I'm having problems getting a Triple Head setup to work right on a new install of Dapper.  I have 2 cards, an AGP 6800GT and a PCI FX5200.  The 2 screens on the 6800GT come up fine, and are using TwinView.  The screen on the 5200 doesnt come up at all (and ive tried putting UseInt10Module in as well for it).

My Xorg.conf is as follows (for the relevant sections) - 

```

Section "Monitor"
    Identifier     "L1915S"
    Option         "DPMS"
    Option		"HorizSync" "30-83"
    Option		"VertRefresh"  "56-75"
EndSection

Section "Device"
    Identifier     "6800GT"
    Driver         "nvidia"
    Option 	   "TwinView" "True"
    Option         "MetaModes" "1280x1024,1280x1024"
    Option         "HorizSync" "30-83"
    Option         "VertRefresh" "56-75"
    Option         "TwinViewOrientation" "RightOf"
    Option         "RenderAccel" "True"
    Option	   "NoLogo" "True"
    Screen	0
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"5200FX"
	Driver		"nvidia"
	BusID		"PCI:2:9:0"
        Screen		1
	Option		"UseInt10Module" "True"
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"5200FX"
	Monitor		"L1915S"
	DefaultDepth	24
	Subsection "Display"
		Depth 24
		Modes	"1280x1024"
	EndSubsection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "6800GT"
    Monitor        "L1915S"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

I have checked the Xorg log file, and these are the relevant sections - 

```

(--) PCI:*(1:0:0) nVidia Corporation NV40 [GeForce 6800 GT] rev 161, Mem @ 0xf4000000/24, 0xd0000000/28, 0xf3000000/24, BIOS @ 0xf5de0000/17
(--) PCI: (2:9:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xf6000000/24, 0xe8000000/27, BIOS @ 0xf7ec0000/17

```

```

(WW) NVIDIA: No matching Device section for instance (BusID PCI:2:9:0) found
(EE) Screen 1 deleted because of no matching config section.

```

Obviously it isnt loading the config for the second gfx card, but I can not see what the actual problem is.  The Device section for the 5200FX looks right to me, and I am specifiying the BusID, yet it still does not pick it up.  Why?

Any help would be much appreciated!

---

### Post by Spleenie on 2006-08-23
You may want to check your bios to see whether PCI snoop is working. I think this tells the computer whether or not to look for PCI video cards and activate them.

---

