---
title: "Dual Screen Setup"
date: 2009-05-06
forum: General Help
---

### Post by duffboy on 2009-05-06
I am currently running Intrepid on a Dell Inspiron 710m. I am trying to correctly configure my dual monitors.

I am trying to configure my 19" 2nd monitor rotated and to be located on the left of my laptop's main screen.

The screens come up the right size, but my 2nd monitor is not rotated. I have to use the randr every time I boot to move my 2nd monitor to the left of my main monitor and rotate it to the left.

If someone could provide some guidance that would be great. Thanks.

I have included my xorg.conf.
```
Section "Device"
	Identifier	"Configured Video Device"
        Option          "monitor-LVDS" "Configured Monitor"
	Option          "monitor-VGA" "19Monitor"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Option "PreferredMode"  "1280x800"
        Option "Position" "900 0"
EndSection

Section "Monitor"
        Identifier      "19Monitor"
	Option "PreferredMode"  "900x1440"
	Option "Position" "0 0"
        Option "LeftOf" "Configured Monitor"
        Option "Enable"  "true"
    	Option "Rotate"  "left"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2180 2240
	EndSubSection
EndSection
```

---

