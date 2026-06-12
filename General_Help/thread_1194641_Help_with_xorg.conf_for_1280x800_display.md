---
title: "Help with xorg.conf for 1280x800 display"
date: 2009-06-22
forum: General Help
---

### Post by Literati on 2009-06-22
Hi all, trying to force my laptop into it's native resolution of 1280x800, but it's just refusing to work :/

Here's my xorg.conf file, any idea what I'm doing wrong?

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
               
	HorizSync      31.5 - 90.0

        VertRefresh      60.0 - 60.0

        Option  "dpms"

  # 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
	Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24

                SubSection "Display"

                  Viewport 0 0

                  Depth 16

                  Modes "1280x800" "1024x768" "800x600" "640x480"

                EndSubSection

                SubSection "Display"

                  Viewport 0 0

                  Depth 24

                  Modes "1280x800" "1024x768" "800x600" "640x480"

                EndSubSection

EndSection
```

---

### Post by Johnny B on 2009-06-22
SubSection "Display" perhaps?

[xorg.conf manual page]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html")

---

### Post by Bachstelze on 2009-06-22
You can't have a 1280x800 resolution using the vesa driver. You'll have to install proper drivers for your graphics card.

---

