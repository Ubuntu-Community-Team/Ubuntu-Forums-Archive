---
title: "awn notification area messed up"
date: 2009-09-27
forum: Desktop Environments
---

### Post by baytuni on 2009-09-27
Hi. I am using jaunty and awn 0.3.2 together on my intel video card. You know all those issues about intel integrated video drivers I really spent so much time. Anyway I was using "uxa" accel method before this problem wasn't there. Then I realized "uxa" is not working for me well, so I went back to "exa" but now the notification area on awn is messed up. (see the image the applet on the very right is systray)
[IMG]http://img62.imageshack.us/img62/5240/screenshotw.png[/IMG]

and here is my xorg.conf

```
Section "Device"
	Identifier	"intel"
	Driver "intel"
        #Option		"UseFBDev"		"true"
        Option		"AccelMethod"			"exa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false"
        Option      "DRI"                    "True"
        Option      "NoDDC"                  "True"

        Option      "EnablePageFlip"         "True"
        Option      "RenderAccel"            "True"

        VideoRam 261120
      
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

---

### Post by baytuni on 2009-10-03
I discovered that this all happens beause of the option ```
Option		"MigrationHeuristic" "greedy"
``` If I turn the option to "always" or "smart" then the notification area works but then again all the animations slows down and the responsiveness decreases. Anybody knows what is the connection between that option and sys tray of awn?

---

