---
title: "ATI drivers + BT878 = no TV?"
date: 2006-01-19
forum: Desktop Environments
---

### Post by crispy_420 on 2006-01-19
OK i just installed the proper ATI drivers but lost my TV watching. The ATI drivers are working perfect but when I lauch tvtime from terminal I get this error:

[PHP]Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /root/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.
[/PHP]

What now? How can I watch TV again? Or how do I enable YUY2 support in ATI drivers?

I know this has probably been answered before, so just send me in the right direction or provide a link.

My hardware:

ATI 9800 Pro 128MB
Leadtek BT878 based card (Winfast Deluxe?)
1024MB DDR
Intel 845 based MB (D845BG)

I missed any thing just ask...

<<It worked perfectly before ATI driver update>>

---

### Post by vruum on 2006-01-19
did you install the ati drivers from synaptic/apt-get? if so how did you configure them? try typing this into a terminal
```
xvinfo
```
if it says something like "no display" or something like that, then add this line to the device section (below the line that says "Driver    "fglrx"")of your xorg.conf 
```
Option "VideoOverlay"               "on"
```

---

### Post by t-bird on 2007-01-27
I have the same problem:

:~$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present


In xorg.conf there is already overlay on

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"


What can i do? :(

---

### Post by t-bird on 2007-01-29
up :(

---

### Post by theorem_hunter on 2007-02-10
so do we need 2 use the open source drivers for ATI?

im gettin a pit pissed... gonna thro my ATI card away & get nvidea... XGL also not working

---

