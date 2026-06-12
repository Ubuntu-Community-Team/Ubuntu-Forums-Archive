---
title: "SiS Video"
date: 2006-04-24
forum: Desktop Environments
---

### Post by steveneddy on 2006-04-24
Help - I have an old Sis 305 video card in my desktop. the vid output works and I get a screen, but no 3D accelleration. When I run glxgears, it runs slow and says server not running. I played with it all weekend.

Here's my xorg.cong file:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"SIS"
	Driver		"sis"
	VideoRam	12580
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"SIS"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


***************************

I DL-ed the driver from [http://www.winischhofer.net/](http://www.winischhofer.net/) - put it in the driver file like it said to. 

Do I need to put the direct path to the driver in the xorg.cong file?

Any help will be appreciated.

-SE

---

### Post by steveneddy on 2006-04-24
I did this today after reading some more on the forums:

Section "Device"
	Identifier	"SIS"
	Driver		"sis"
	BusID		"PCI:0000:01:0a.0"
	VideoRam	16384
	EnableSiSCtrl   "yes"
EndSection

********************

I altered the video ram, added the correct PCI bus address according to lspci and added the line to enable the SiS control GUI, but still no luck.

Here is the output from trying to run glxgears:

glxgears
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
X connection to :0.0 broken (explicit kill or server shutdown).

***************************

New education - what is fbconfigs?

Thanks to anyone who can help.

---

### Post by az on 2006-04-24
Try exiting X
CTRL-ALT-F1
login
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
(and set your resolution to 800x600 at 16-bit color.)

sudo /etc/init.d/gdm restart
and see of you have acceleration at that resolution and depth.  X cannot de-allocate memory on-the-fly, so maybe that's why you have no DRI.

also, post the output of

 cat /var/log/Xorg.0.log|grep EE

---

### Post by steveneddy on 2006-04-26
Hey Azz...I've seen you post all over the forums regarding the SiS vid cards and I appreciate you answering my post. Thank you.

I've decided to ditch the SiS card for a vid card with the Nvidia chipset. I found the SiS card problematic and not well supported within Linux.

I hope I am going in the right direction. It just seems that an Nvidia chipset would be a better supported in this machine, and...well...I've always had onboard video, so this is really my introduction to video cards. Wish me luck.

Is there anything I need to know or do before trying this option?

Also, do I need to disable the onboard video section of the MB, and how do I do that?

Onboard video chip is an Intel i810. 512mb of system RAM. Processor is an Intel PIII, 935mhz. I don't have an AGP slot, so I HAVE to go with the PCI card. Dell monitor, 17" set at 1024X768. I believe that it is capable of slightly higher resolution with the correct video driver.

Thank everyone for their help on this one.

---

### Post by az on 2006-04-26
[QUOTE=steveneddy]

Is there anything I need to know or do before trying this option?

Also, do I need to disable the onboard video section of the MB, and how do I do that?

Onboard video chip is an Intel i810. 512mb of system RAM. Processor is an Intel PIII, 935mhz. I don't have an AGP slot, so I HAVE to go with the PCI card. Dell monitor, 17" set at 1024X768. I believe that it is capable of slightly higher resolution with the correct video driver.

Thank everyone for their help on this one.[/QUOTE]

I beleive that the onboard intel i810 will give you much better performance than the sis card anyway - sis sucks even in windows.

DRI is enables out-of-the-box for i810 and is 100 percent GPLed (free software) where the nvidia drivers are binary-only.

In your bios, you may have the option to set the default video card.  The factory set setting for that would be to look for a pci card and use that if there is one there.  That way, so long as you don't have a pci video card inserted, you will use the onboard anyway.  If something happens to your onboard video (broken pins or something) you don't have to go into the bios blindly to be able to use the pci card.

Just be sure that setting is still set to pci.

And to reconfigure any video card in ubuntu, boot into recovery mode and run

dpkg-reconfigure -phigh xserver-xorg
and then run
init 2

---

### Post by steveneddy on 2006-04-30
Thanks, Azz, for all of your help. I have printed all of your tips for reference and have sucessfully installed a new nVidia card. GeForce FX 5200. It's not the best vid card around, but it does give me better video and a nicer looking screen. I was able to install all of the nVidia device drivers through the Help section of Ubuntu. I added the Help section and online advice together to get a very nice instruction sheet to use next time this happens. 

BTW, my BIOS doesn't give me the option of turning off the onboard video.

Another note, the PC is an old HP PIII w/ 512 mb RAM, blah, blah.....the best way I got the card to finally come up was to leave the PCI address blank while trying to set up oxorg and let the OS determine where the card was installed. After that, it was all a breeze. 

My Windows has crashed since the installation of the Nvidea card, probably b/c of the vid card, so I have seen online, so.....I'm installing Dapper Flight 6 on the partition where Windows was previously installed.

Anything I need to know about Dapper pre-release that would relate to the nVidia card?

Much regards. 

-SE

---

