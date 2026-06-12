---
title: "Boot without monitor attached in Intrepid?"
date: 2008-11-29
forum: Desktop Environments
---

### Post by chaeron on 2008-11-29
Before upgrading to Intrepid, I used a custom xorg.conf file to set a default monitor size.

After the upgrade, that xorg.conf file doesn't seem to work and in fact, was replaced by a generic one with nothing in it.

Problem is that I have a number of machines hooked up to a KVM switch, so there are times when I will reboot a machine (using VNC) that doesn't have a physicial monitor attached.  X then barfs and shows an error message and stops the boot process!

Any ideas on how to set the default monitor stuff in Intrepid (no joy out of the Screen Preferences Gnome app) so that X will boot properly even if the monitor isn't attached?

1 step forward and 2 back it seems...

Thx!

---

### Post by nikgare on 2008-11-29
I believe you have to do the same as with 8.04 - ie create a custom xorg.conf file.
Do you have a copy of your previous xorg.conf file? it may be as simple as just copying it over.
Other wise the documentaion here [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy) might help.

---

### Post by chaeron on 2008-11-29
Tried using the old Hardy xorg.con file....it errors out, so that's a no-go.

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

Tried using just the above Monitor/Screen settings, but that errors as well.

Real PITA.

I'll check the link you posted, but given that it's for Hardy and it seems a lot of X stuff changed with Intrepid, I'm not holding my breath.

Could use some guidance from a real X11 expert that knows Intrepid.  <hint, hint> ;-)

This shouldn't be all that difficult I would think, since a lot of folks out there us KVM's to share monitors/mice/keyboards and use VNC from a central machine rather than physicial devices.

---

### Post by chaeron on 2008-12-03
Anyone know how to configure Intrepid and the new X to boot Ubuntu Desktop without a monitor attached????

Thx!

---

### Post by trtr on 2009-02-01
I have the same problem.

No solution?? :(

---

### Post by chaeron on 2009-02-01
Not yet...guess the X guys don't track the Ubuntu forums.

Kind of a piss off that they changed this and have left us high and dry.

---

