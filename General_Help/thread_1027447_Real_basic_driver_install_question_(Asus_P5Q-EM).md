---
title: "Real basic driver install question (Asus P5Q-EM)"
date: 2009-01-01
forum: General Help
---

### Post by Up2Late on 2009-01-01
Just installed Linux Mint on my Asus P5Q-EM Motherboard (intel G45 chipset).

It's hooked up to my 52" Samsung LCD via HDMI

FYI (all following issues work fine in Windows, so not a hardware issue)


***Issues:

- Sound is not working at all.  I have no HDMI option under "Sounds"
- Video runs awful.  Not just HD, but even hulu
- Have NO IDEA what to do with the linux sound driver I downloaded from Asus


***Driver Installation???

- I have no idea what to do with the .tar.bz2 file
- Under "Hardware Drives", it just reads "No Proprietary Drivers ..."

***Questions

- What the heck do I do with that file (several others in different folder were unzipped as well)?

- There seems to be another driver I can download for the GPU from "Intel Linux Graphics".  Anyone tried that with any success?


FYI, the Linux Drivers package from asus also included LAN drivers, but I'm having no issues there.

Thanks

---

### Post by densou on 2009-01-01
I think G45 support is still preliminary ( [http://intellinuxgraphics.org/testing.html](http://intellinuxgraphics.org/testing.html) )

well, first you need to find if you're using generic VESA driver (it could happen if Intrepid doesn't recognize the card during install) looking to xorg.conf   
open a prompt window, type *sudo gedit /etc/X11/xorg.conf* press enter then type root password when asked (invisible chars)

or try mine after made a backup of yours (of course rename this one into xorg.conf :P )
[http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new)

it works after a complete reboot or ctrl+alt+backspace (reboot only X server)

afterwards, it could be necessary to SET which resolution (and which output) you desire as the default one

---

### Post by Up2Late on 2009-01-01
Sorry, but all I get when I open xorg is:

---------------------------------------

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

-------------------------------------------------------

Don't know if this helps.  Also, why can't I figure out how to install a driver???  I've searched for hours, and nothing.  Why can't I do anything from "Hardware Drivers"?

---

### Post by densou on 2009-01-04
> **Up2Late said:**
> ```
Section "Device"
	Identifier	**"intel"**
        **Driver**          **"intel"**
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

it should be enough to modify into what I added in bold chars. 
(remember to open xorg.conf with the line 'sudo gedit /etc/X11/xorg.conf' or you can't edit it)
[complete reboot is required, or simply press Ctrl+Alt+Backspace, X server will restart]

> Don't know if this helps.  Also, why can't I figure out how to install a driver???  I've searched for hours, and nothing.  Why can't I do anything from "Hardware Drivers"?

Because Intel updates are provided by the community, ATI and nVidia have both a closed driver and an open one.

Add these lines on Synaptic (packet manager) as third-party repositories:
deb [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/intel-gfx-testing/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ubuntu) intrepid main


P.S. HDMI suffers several bug with G35 and newer (G4x), the 'no sound' issue is widely known. A good resource: (maybe it requires a further knowledge of Gnu/Linux systems)
[http://bugs.freedesktop.org/show_bug.cgi?id=19292](http://bugs.freedesktop.org/show_bug.cgi?id=19292)

---

