---
title: "Xorg video problems on new install"
date: 2008-02-23
forum: Desktop Environments
---

### Post by degreseven on 2008-02-23
Hello, 
I'm having a video problem with X. I was unable to use the livecd to install- I would see the ubuntu loading screen & then when X started up I would just get a bunch of jumbled colored blocks & stripes. I ended up using the alternate CD to install, assuming it was a problem with the livecd. Apparently it is not, as I am still unable to use X. I got the nvidia driver installed & tweaked my xorg.conf, but no luck. Now when I start X I see the nvidia logo, the screen goes black, nvidia logo comes back... this happens a few times, & then I finally get dumped into X where the screen is all distorted with colored bars. I can barely make out the top of an error saying something about "unable to determine video....something" 

This is using an nvidia geforce 4 mx440 with svideo out to my tv. I'm trying to run it in 640x480, but have tried other resolutions as well. I know the hardware works because I was previously running gentoo on this same setup with X working just fine. I was using an older version of Xorg on the gentoo install (7.0 maybe), so maybe something changed in the newer versions that's messing me up? 

Here is my xorg.conf:

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoRenderExtension" "1"
	Option		"RenderAccel" "0"
	Option		"TVStandard" "NTSC-M"
	Option		"TVOutFormat" "SVIDEO"
	Option		"TVOverScan"	"0.6"
	Option		"ConnectedMonitor" "TV"
EndSection

Section "Monitor"
	Identifier	"TV"
	#Option		"DPMS"
	Option		"UseEdidDpi" "FALSE"
	Option		"DPI" "100 x 100"
	#HorizSync	28-51
	#VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"TV"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		1
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		4
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		8
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		16
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

The Xorg log file shows no errors or warnings. Any help with this would be *greatly* appreciated. I miss having my mythbox! =)

Thanks in advance.

---

### Post by degreseven on 2008-02-23
bump. Really, *any* advice would be great.

Thanks

---

### Post by Azzco on 2008-02-24
Got the exact same problem..
I had the same problem with Fedora 8 liveCD, I had to unplug my nvidia card to install and when the installation was done it worked fine. But I had the same luck as you on ubuntu.

Funny thing is that I have a portable HD with kubuntu on it. Got very similar hardware in school as on my PC. The ubuntu install on my HD works fine in school but not at my PC. The same drivers applies for both the card in school and the one on my PC.

Might aswell add that I have a GeForce 7600 GS.

---

### Post by degreseven on 2008-02-24
Sorry, not sure I understand. Fedora worked for you after it was installed, but you never got the issue resolved on ubuntu?

Pretty weird about your portable hdd... Do you know if the nvidia driver versions were the same at school & at home?

---

### Post by Azzco on 2008-02-24
> **Azzco said:**
>  The same drivers applies for both the card in school and the one on my PC.

Yupp same driver version.

After some forum searches I came to the knowledge that there's a problem with jmicron found on Asus P5B motherboards... I have no idea what jmicron is but I have a P5B.

I have no problem with the older livecds. I wonder what's wrong.

---

### Post by degreseven on 2008-02-24
I have no idea what jmicron is either, but I have an Abit vt7, so apparently it's not specific to the ASUS p5b...

---

### Post by degreseven on 2008-03-08
Well I just tried fedora & had the same problem. I also looked up the jmicron thing you were talking about. It looks like that's a sata controller & seems unrelated. People having problems with jmicron controllers were not able to mount partitions. This seems more like a bug in X, but it seems odd to me that any hardware other than the video card would affect X.

---

