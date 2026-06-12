---
title: "How to increase my resolution"
date: 2007-03-01
forum: Desktop Environments
---

### Post by lsutiger on 2007-03-01
Hi All! I am wondering how to axamize my desktop resolution. At the moment I just have the basic ubuntu loaded. The largest screen size available is 1024X800, but my screen will go up to 1280x1024.
Thanx in advance!

---

### Post by AlcoJaguar on 2007-03-01
You'll need to add new resolutions to your specific color depth in the xorg.conf file.

First you'll want to back up your current configurations, type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then use gedit to open your configuration for editing:
```
sudo gedit /etc/X11/xorg.conf
```

Down near the button where it says 'Section "Screen"' you'll see SubSections called "Display" (something like this, but you'll probably have different device information):
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	Option		"AddARGBGLXVisuals" "True"

	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		32
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Go ahead and add resolutions to those Display SubSections for the color depth you want (If you're not sure what color depth you use it's safe to add the resolutions to all color depths, though for a depth of 8 is might look like trash :) ). 

Restart your system or if you want you can hit ctrl+alt+f1, log in, and type:
```
sudo /etc/init.d/?dm restart
```

This will restart your XServer and bring you back to your normal login.

You should now have more resolution options in System->Preferences->Screen Resolution.

Hope this helps.

---

### Post by lsutiger on 2007-03-01
Heres what I have in that section:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x720 1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x720 1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x720 1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x720" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x720" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x720" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```
I am guessing that I need a driver first...Where can I find one for my seific chipset?
lspci gives me this:
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
Thanx for the help! (I can't believe I remembered a command! YAY!
baby steps...

---

### Post by AlcoJaguar on 2007-03-01
You gotta crawl before you can walk :) . 

Yup, you found the correct section. To be honest with you I have no idea what driver you'd need to install for a Silicon integrated chip (you might very well be stuck with vesa). You don't *need* the driver to use different resolutions but it is nice to have direct rendering. Go ahead and change:
```
SubSection "Display"
		Depth		1
		Modes		"1280x720 1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x720 1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x720 1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x720" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x720" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x720" "1024x768" "800x600" "640x480"
	EndSubSection
```
To:
```
SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x720 1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x720 1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x720 1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x720" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x720" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x720" "1024x768" "800x600" "640x480"
	EndSubSection
```
Notice I just added "1280x1024" to every list of resolutions.

Once you've done that, follow the rest of my directions from my last post and you should be able to use 1280x1024 as your resolution.

After that, if you're feeling adventurous, you can try out the Envy script at [http://lunapark6.com/?p=2717]("http://lunapark6.com/?p=2717"). I have to warn you I don't know what driver your video chip should use but I just thought I'd supply that link to help you start exploring. I'm pretty sure Envy will detect your chip and take the appropriate actions but don't do anything you're not sure of. It's better to have a working desktop with no direct rendering than no desktop at all :) .

---

### Post by lsutiger on 2007-03-01
Thanx! I trully appreciate the help! Got my screen to the right resolution, but it just doesn't seem as 'crisp' as it should be. I will try that and get back to ya!
Merci!

---

