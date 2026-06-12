---
title: "How I got Ubuntu to use my monitor's maximum resolution"
date: 2007-05-27
forum: Desktop Environments
---

### Post by vodsonic on 2007-05-27
Here is how I got Kubuntu to use the full resolution of my new, larger monitor (1280x1024), when before the highest option was only 1152x864. It seems that this problem, and variations on it, are quite common, so I've decided to post my solution here. I'm guessing that this applies particularly to older embedded graphics cards.

I have a yard-sale Compaq with an 800 Mhz CPU. I used to use it for testing different Linux distros, but now would like to turn it into a desktop for a non-techie family member. I originally installed Xubuntu 6.10 for this purpose. During the install, I used a smaller, 1024x768 monitor, which I later replaced with a newer 19" Samsung with a native resolution of 1280x1024. At that point, Xubuntu would only output 1024x768, and this was the maximum setting available in Xfce's display settings.

I tried adding "1280x1024" in the relevant places in /etc/X11/xorg.conf. No dice. I also tried running

sudo dpkg-reconfigure xserver-xorg

Again, with no joy.

I then determined that Kubuntu would work better for me, so I formatted the old Xubuntu partition and installed Kubuntu 7.04 instead. Kubuntu would output a maximum screen resolution of 1152x 864. This was slightly better than what Xubuntu had been doing, but still not up to the full native resolution of the monitor. I tried the same things I had done with Xubuntu, again with no success. I also tried 

sudo dpkg-reconfigure xserver-xorg -phigh

This added one slightly larger screen resolution to the available options in the display settings, but STILL not the full resolution of my monitor.

I rebooted into a Puppy Linux 2.13 live CD to see how that distro would handle my graphics card and monitor. It was able to do 1280x1024x24, but it was fuzzy and jittery - instant headache recipe. I then tried 1280x1024x16, which worked great.

I rebooted back in to Kubuntu, opened /etc/X11/xorg.conf as root, and under 'Section "Screen"' changed the value of DefaultDepth from 24 to 16. Saved the file and rebooted. 

Bingo - I now have a 1280x1024 desktop.

I suspect that the older embedded graphics on this old box do not support 24-bit color depth at such a high resolution. Dropping the color depth to 16 did the trick. 

-----------------------------

The relevant portion of my xorg.conf looks like this:

> Section "Device"
	Identifier	"ATI Technologies Inc 3D Rage Pro AGP 1X/2X"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc 3D Rage Pro AGP 1X/2X"
	Monitor		"SyncMaster"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection 

---

### Post by GimmeDecaf on 2007-05-27
Thanks for the post, but it didn't work for me. I've tried pretty much all the options out there to get my resolution up to 1400x900 but I just can't get that option to show up. Here's my xorg.conf, if anything stands out for you please let me know:
```


Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 420]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"A912WDB"
	HorizSync	30.0 - 82.0
	VertRefresh	56.0 - 76.0
	Option		"DPMS"
	Option		"ModeValidation" "NoMaxPClkCheck"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 420]"
	Monitor		"A912WDB"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1440x1440"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1440x1440"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1440x1440"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1440x1440"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1440x1440"	"1400x900"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1440x1440"	"1400x900"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection


```

I added the HorizSync and VertRefresh rates after looking up [this post]("http://www.cyberciti.biz/faq/howto-use-linux-ddcprobe-command/")

Thanks
Amit

---

### Post by AkriaII on 2007-05-28
Thanks dude!  I was looking for a solution for the past 2 hours with no luck and editing the xorg.conf file did the trick... :D

by the way, since it's normally protected, use:

sudo gedit /etc/X11/xorg.conf

There was a post before that mentioned that Ubuntu looks for the screen before it assigns a resolution, and I think there may be some truth to that.  Haven't looked too closely, but I'll putz around some more and see if I find anything...

Thanks again

---

