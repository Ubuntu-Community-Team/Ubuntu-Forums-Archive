---
title: "video performance problem"
date: 2007-03-26
forum: Desktop Environments
---

### Post by clinto on 2007-03-26
I'm a noob, so please forgive me if I talk about this subject in an elementary way. I'm also trying to write this thread so other noobs with the same problem might learn from my learning experience.

I've been having problems ever since I've installed Ubuntu Edgy(6.10) with slow frames. That is, when I use programs like Firefox, my primary web browser, and I scroll down the page, it jumps instead of scrolling smoothly. I've noticed also that other programs are affected by this action, such as audio programs. Example: If I'm playing music and I scroll down in Firefox, my music haults until I'm down scrolling.

Being a noob, the first things I thought were, either it was a)my processor was too slow, b)my /swap directory was too small, or c)I was having some problem with Firefox. As I researched, I found that it couldn't have been my processor, since a Celeron 2.4 performs well enough to handle anything Ubuntu could dish at it. I found my /swap file was about 630Mb and I have 512Mb of RAM, which is apparently enough to handle paging. A friend told me my problem was probably due to Firefox using flash and that I needed to modify some options. But after talking to people I found it was probably due to my lacking an appropriate video driver.

One way I found this out was when someone told me to open Terminal and type:
glxgears
This opened a little program that displays gears and shows the user how well the video is running on your system[(click here to see a screenshot)](http://i149.photobucket.com/albums/s74/clintonkoenig/glxgears.png). When I did this, my gears weren't running smoothly. Instead, they were pulsating, moving about twice a second.

Drivers are something new to me. I've never installed them. I've never even read about them. So the first thing I needed to do was learn what kind of video card my pc was using. I did this by going under System>Administration>Device Manager. [You can see a picture of what my device manager looked like here.](http://i149.photobucket.com/albums/s74/clintonkoenig/Screenshot-DeviceManager.png) When the device manager was opened, I scolled down until I saw something that resembled something to do with video. Near the top, I saw something that said "Sis AGP port(PCI to PCI bridge)." Under this it said "661/741/760/761 PCI/AGP VGA display." HOWEVER, when I looked under Windows XP, it told me "Sis 650/651/740/661FX/741/760." I am still unclear why the two different operating systems say different things, let alone why my system is telling me so many different versions.

So, I went [here](http://www.sis.com/download/agreement.php?url=/download/) and entered my system information and found [this](http://www.sis.com/download/download_step1.php). Sis 650 Graphic Driver(Redhat 7.0 and 7.2) was all that was provided for Linux. Redhat is a different Linux distro, however. I proceeded to download the 7.2 version and the file is currently sitting on my desktop like a lost child.

Is this the correct driver to install? Windows XP said my videocard included Sis650, but Ubuntu didn't. On top of that, Redhat is in the title. If this is the correct file, how do I proceed to install it?

---

### Post by codesplice on 2007-03-26
Hi,
A quick search revealed [this thread](http://www.ubuntuforums.org/showthread.php?t=384232) which briefly goes over what needs to be done.

[http://www.winischhofer.eu/linuxsisvga.shtml](http://www.winischhofer.eu/linuxsisvga.shtml) has some more information on Sis drivers and using them under Linux.

I'm assuming that the file you downloaded is in a *.rpm format (Redhat Package Manager)?  This won't work natively on Debian-based systems, but there is a way around that.

Use Synaptic (or your package manager of choice) to install a packaged called "alien".  Alien will allow you to convert *.rpm files to *.deb, which you can then simply double-click and run.  

The command for using alien to covert the rpm into a deb is as follows:

```
sudo alien -d <insert rpm filename here>
```

More information on alien can be found [here](https://help.ubuntu.com/community/RPM/AlienHowto).

Hope this helps :)

---

### Post by will_in_wi on 2007-03-26
Can you post /etc/X11/xorg.conf and the output on the dmsg command?

---

### Post by clinto on 2007-03-27
Thank you very much codesplice.

I'll get back to you guys on Wednesday or Thursday when I've returned to my pc.

---

### Post by jocko on 2007-03-27
I'm not absolutely sure about this, but I think ubuntu already has the drivers you need.
Open up a terminal and copy/paste the following command:
```
sudo dpkg-reconfigure xserver-xorg
```
That will start up a configuration program that allows you to select which video driver to use. In the first screen select "sis" and accept the default answers to the rest of the questions.
Restart the xserver by pressing ctrl-alt-backspace or reboot the computer.
If it would not work and leave you in a command line interface, you can fix it by typing the same command again and select "vesa".

---

### Post by clinto on 2007-03-29
this is my xorg.config.
===========================
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 107G"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"PHILIPS 107G"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
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
=====================
I used "dmsg" and it wasn't recognized as a command, I'll look further to find what you meant.

I'm going to follow through with what jocko said and I'll get back.

---

### Post by clinto on 2007-03-30
Okay, the problem seems to be fixed. The problem was that the video driver that was automatically loaded at installation was "vesa" instead of "SiS." I used the previously provided command...
sudo dpkg-reconfigure xserver-xorg
which allowed me to change the driver from "vesa" to "SiS." After this, it asks further questions about your video card and monitor information. Another thing that was wrong was my resolution. It seems it was set higher than 1280x1024, which is all my 15" monitor can handle. It sucks working in a lower resolution, but it's an even trade for the performance difference.

The only thing I'm still unsure of is that, when I use...
glxgears
the frames per second are even slower now, going at about .5fps. Is it possible I still haven't set up my video correctly? Everything else seems to be working fine.

---

### Post by clinto on 2007-03-30
I typed in the command...
glxinfo
... and noticed...
Direct Rendering: No
... which means the "SiS" driver suplied by Ubuntu doesn't have any form of acceleration. So I've been advised to download a driver, which I already have, and try using it instead.

Codesplice commented earlier that the driver I had downloaded is probably in .rpm format and that it needs to be converted to a .deb format. However, I'm unsure of how to identify the file's format. In the properties, it only calls it an "object code." The name of the file is "sis_drv.o-410". Can anyone shed light on this?

I've also been advised to leave things be and not worry about acceleration. This person told me that installing such a driver wouldn't be as stable, that I'll just run into problems down the road. He then said, on the other hand, it would be good learning experience if I'd be willing to venture. I'm not sure if I should take his advice or not.

---

### Post by lxop on 2007-09-22
I believe what you have is a .bin file, and I'm not entirely sure what to do with that.  However, I have an SiS760 card working fine (I don't do gaming on Linux for the record), with the standard drivers from the repository.  I have run  'sudo dpkg-reconfigure -phigh xserver-xorg' and set my driver to sis and my resolutions to what my screen can handle (1280x800), and its good as gold

---

