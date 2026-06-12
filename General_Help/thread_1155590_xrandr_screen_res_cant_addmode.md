---
title: "xrandr screen res cant addmode"
date: 2009-05-10
forum: General Help
---

### Post by max_power on 2009-05-10
Im trying to add 1280x1024 to my laptop. Here are the steps im taking:

Please Note the errors in the results of step 2 and 3

1st
```
$ gtf 1280 1024 59.9

  # 1280x1024 @ 59.90 Hz (GTF) hsync: 63.49 kHz; pclk: 108.70 MHz
  Modeline "1280x1024_59.90"  108.70  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

```

2nd
```
$ xrandr --newmode "1280x1024_59.90"  108.70  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

xrandr --newmode "1280x1024_59.90"  108.70  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 ()
  Serial number of failed request:  25
  Current serial number in output stream:  25


```

3rd
```

xrandr --addmode LVDS 1280x1024_59.90X Error of failed request:  BadMatch 

(invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 ()
  Serial number of failed request:  25
  Current serial number in output stream:  26

```

Here is my xorg.conf
[PHP]
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1280 1024 #1792
	EndSubSection

EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option "RandRRotation"
EndSection
[/PHP]

Video card ATI Radeon Xpress 200m

Thanks

---

