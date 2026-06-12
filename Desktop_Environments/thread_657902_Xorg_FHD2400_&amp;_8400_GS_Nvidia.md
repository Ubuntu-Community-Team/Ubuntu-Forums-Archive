---
title: "Xorg FHD2400 &amp; 8400 GS Nvidia"
date: 2008-01-04
forum: Desktop Environments
---

### Post by zpro on 2008-01-04
Running 7.10 on my new X-Mass hardware sweet,
however, the setup with the restricted drivers went okay, but need some tweaks,
I notice a few things where okay, but wanted to make sure the setting for the monitor was correct:

As you can see from below the max Vertical Freq is not set @74 Hz
and the max Horizontal Freq is not set @60 KHz
the question is where would I put this ?

Thanks-:)
--------------------

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8400 GS]"
	Boardname	"nv"
	Busid		"PCI:4:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"

  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8400 GS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1920x1200@60"	
	EndSubSection
EndSection

---

### Post by zpro on 2008-01-04
<New Year Bump>

---

### Post by PmDematagoda on 2008-01-04
Open Nvidia Settings using:-
```
sudo nvidia-settings
```

You can then do the necessary changes.

---

### Post by zpro on 2008-01-04
Thanks, after running the nvidia setup control panel,
now I get this in my xorg.conf

    Identifier     "Generic Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Gateway FHD2400"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8400 GS]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8400 GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1920 1200
        Depth       24
        Modes      "1920x1200@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1200_60 +0+0"
EndSection
-------------------------------------------------------------

Does this look normal :confused:
having two monitor section and two screen section ?

should I have uncheck append to xorg.conf ???

Major Thanks-

---

### Post by PmDematagoda on 2008-01-04
The xorg.conf looks ok and there should not be any problem with the way it currently looks. Is your problem solved now?

---

