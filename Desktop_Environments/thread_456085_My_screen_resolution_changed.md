---
title: "My screen resolution changed"
date: 2007-05-27
forum: Desktop Environments
---

### Post by nicenick on 2007-05-27
Ubuntu 6.06, Desktop, PCChips A31G motherboard, Intel Celeron D 336. No Video card, I use the built in VGA driver of the motherboard.

I have been using Ubuntu trouble free for about 6 months.  Last week I downloaded 'Google Earth' for Linux.  It worked fine, but slowly. Google Earth told me to update my vieo driver, I replied "NO".  My computer worked fine for two more days.  Then... The Ubuntu splash screen worked normally and appeared fine. When the time for the 'login' screen came the monitor goes black, I hear the ubuntu sound for login.  If I press [crtl] [alt] [+] two times I get a very distorted screen, press two more time I get a 'huge display' about 4 screens full.  All other [ctrl][alt][+] gives me black screen.

I tried 'sudo gedit/etc/x11/xorg.conf, but the file does not exist on my system (or is not in this place)
I used Synaptic Package Manager to install/reinstall xorg-driver-fglrx and other fglrx packages, but this did not help

[System] [Preferences] [Screen Resolution] shows 1024 X 768, Refresh rate = 0 and can not be accessed or changed.  The other two resolution choices 640X480 and 800X600 give me black screen if I choose them and click reply.  I have tried the check box for "Make default for this computer only checked and unchecked.

How do I get my screen resolution back to everything on one screen?

By the way, I use an ancient OPTIQUEST Q41 CRT Monitor.

In review, the initial ubuntu splash screen looks perfect, then everything goes wrong.

Regards,

Nice Nick

---

### Post by poohbear1616 on 2007-05-27
> I tried 'sudo gedit/etc/x11/xorg.conf, but the file does not exist on my system

Put X11, not x11.

---

### Post by nicenick on 2007-05-28
Thanks, found it, but now know I do not understand it.

Here is the Video Section of my X11/xorg.conf file.  I am at a complete loss as to any of the items shown here. I am afraid to make any 'unassisted' changes. Any help would be appreciated.
Again to recap, I do not have a video card installed, using the Motherboard build-in VGA.

My [system][preferences][screen resolution] has available:
1024x768
800x600
640x480
Refresh Rate is zero and cannot be changed

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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

Regards,
Nice Nick

---

### Post by poohbear1616 on 2007-05-28
Lets try this first.

```
sudo dpkg-reconfigure xserver-xorg
```

It will ask some questions. Answer them as best as you can.

---

