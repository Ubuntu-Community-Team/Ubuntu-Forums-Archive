---
title: "Resolution"
date: 2005-01-12
forum: Desktop Environments
---

### Post by KoolDrew on 2005-01-12
When I go to **Computer > System Configuration > Screen Resolution**  I can only choose a max resolution of 1024x768 @ 85Hz.  I just installed ubuntu and I am very used to having windows at 1280x1024.  However with my 17" CRT I have to run the refresh rate pretty low but that has never bothered me.  Is there anyway I can increase ubuntu to this resolution and use a lower refresh rate?

---

### Post by wallijonn on 2005-01-12
Rerun /usr/X11R6/bin/xf86config or /usr/X11R6/bin/xf86cfg.

---

### Post by KoolDrew on 2005-02-04
[QUOTE=wallijonn]Rerun /usr/X11R6/bin/xf86config or /usr/X11R6/bin/xf86cfg.[/QUOTE]
 When I run **/usr/X11R6/bin/xf86cfg** and then change the resolution I try to save it and it said it failed.  I also tried editing the file manually and I cannot type anything.

---

### Post by 3spades on 2005-02-04
try dpkg-reconfigure xserver-xfree86

---

### Post by jdodson on 2005-02-04
[QUOTE=KoolDrew]When I run **/usr/X11R6/bin/xf86cfg** and then change the resolution I try to save it and it said it failed.  I also tried editing the file manually and I cannot type anything.[/QUOTE]

what kind of video card do you have?  i have nvidia and by default i could only go 1024x768.  i installed the 3D proprietary drivers and i got way higher.  i can't go very high because of my monitor though.  

anyways, check your video card, then install the proprietary drivers accordingly.

[http://www.ubuntuguide.org](http://www.ubuntuguide.org) - for a good way to get the nvidia drivers working.

for the ATI drivers, do a forum search.

---

### Post by crane on 2005-02-04
in terminal window type this:

sudo gedit /etc/X11/XF86Config-4 

then when gedit opens edit this area

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-49
	VertRefresh	43-72
	Option		"DPMS"

set the HorizSync and VertRefresh to what ever your monitor spec say the click save and restartX (ctrl>alt>backspace)

That sbould  let you change your setting then.

---

### Post by Anubis on 2005-02-04
sudo gedit /etc/X11/XF86Config-4



Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

This is what I changed. Add the higher resolution you desire like show above. I had your problem in reverse though.

Gnome would not keep my resolution @ "1024x768"/
 :mrgreen:

---

### Post by jnoreiko on 2005-02-08
[QUOTE=crane]set the HorizSync and VertRefresh to what ever your monitor spec say the click save and restartX (ctrl>alt>backspace)[/QUOTE]

This worked very nicely.
I've not yet been brave enough to add higher resolutions to the file, but at least I can get 1024x768 at a refresh rate that doesn't give me a headache!
Thanks :)

---

