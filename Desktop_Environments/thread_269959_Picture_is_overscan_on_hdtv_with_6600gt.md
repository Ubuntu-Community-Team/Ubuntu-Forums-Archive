---
title: "Picture is overscan on hdtv with 6600gt"
date: 2006-10-02
forum: Desktop Environments
---

### Post by TheHH on 2006-10-02
Hi guys,

I have a HDTV LG 37 " and a nVidia 6600gt connected with the component video out cable.

After reading a lot on this forum and on google I got a 720p picture to work on my HDTV, the only problem is that is overscan, the edges are cut off so I can't see the taskbar nor the mainbar, the resolution that seem's to work widescreen is 1280x720, this is the one I'm using but it is overscan.

I was rreading a post of someone saying untill now there is no way to fix overscan on nvidia 6600gt video card..

I was wondering if somebody has the same videocard and had been successful with underscaning or fixing this issue.

Here is my xorg.conf: THX!


Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	 Identifier     "TV[0]"
	 HorizSync       30.0 - 50.0
         VertRefresh     59.0 - 61.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Monitor		"TV[0]"
	DefaultDepth	24 
        #Available component video modes: 
        #HD480i, HD480p, HD576i, HD576p, HD720p, HD1080i, HD1080p
        Option         "TVStandard" "HD720p"
        Option         "UseDisplayDevice" "TV-0"
        SubSection     "Display"
	  Depth       24
          Modes    "1280x720"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by dk5151 on 2006-11-06
bump...I'm having the same issue. Anybody know of a fix?

---

### Post by kylevan on 2006-11-10
I read about a program called xvidtune 

> Some linux (xterm)utilities which might help you in getting correct modeline for your Monitor/HDTV

xvidtune: It allows you to shrink, expand and move your screen. When you are satisfied with your screen, it will generate ModeLine for you. 

[http://gentoo-wiki.com/HOWTO_Xorg_HDTV](http://gentoo-wiki.com/HOWTO_Xorg_HDTV)

I'm hoping this will work for me.

another suggestion from that page is to use costom-height panels on all sides of the screen so that windows can't maximize beyond the edges.

---

### Post by TheHH on 2006-11-14
I'm gonna try that, but now I'm wondering if thenew release 6.10 has fix this? or maybe it's the driver not doing the right thing?

---

