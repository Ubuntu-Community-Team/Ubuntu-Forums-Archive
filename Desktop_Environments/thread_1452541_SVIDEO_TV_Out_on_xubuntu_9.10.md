---
title: "SVIDEO TV Out on xubuntu 9.10"
date: 2010-04-12
forum: Desktop Environments
---

### Post by BJ_Covert_Action on 2010-04-12
Hello All,

I am trying to hook up an older PC running xubuntu 9.10 to an older rear screen projection TV with an S-video cable. At one point, I had Ubuntu 8.04 installed on the same PC, connected to the same TV, but it was buggy and kept crashing. As such, I decided to wipe the old Ubuntu install and try a more modern, less resource intensive operating system. Hence my move to xubuntu for this particular machine.

Anyways, long story short, I installed xubuntu and it is running beautifully. It seems to have picked up the correct open source drivers for the ASUS manufactured, Radeon 9600 video card inside the PC. I connected a VGA, LCD monitor to the PC, as well as the S-video TV so that I could configure the system. Currently, I can see the boot up on both screens simultaneously. However, as soon as X loads, the TV screen goes blank and only the LCD screen continues to show anything. 

At first, I thought this was a resolution error that could be fixed by manually controlling the resolution possibilities in the xorg.conf file. As such, I homebrewed my own xorg.conf file and put it in the /etc/X11 directory as I assume is appropriate (for reference, this is a bit of a followup _[to my previous thread).](http://ubuntuforums.org/showthread.php?t=1452477)_ The contents of my current xorg.conf file are posted below:
```

Section "Device"
	Identifier	"Radeon_9600"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"TVStandard" "NTSC-M"
	Option		"ConnectedMonitor" "TV"
	Option		"TVOutFormat" "SVIDEO"
	Option		"XAANoOffscreenPixmaps"
	#Option		"ForceCRT2Type" "SVIDEO"
EndSection

Section "Monitor"
	Identifier	"Rear_TV"
	Gamma		1
	#Vendorname	"Plug 'n' Play"
	#Modelname	"Plug 'n' Play"		
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 800x600"
	#Horizsync	31.5	-	35.1
	#Vertrefresh	50.0	-	61.0
	#modeline  	"640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	#modeline  	"800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"TV_Screen"
	Device		"Radeon_9600"
	Monitor		"Rear_TV"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"800x600" "640x480"
		Virtual 800 600
	EndSubsection
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"dead"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen		"TV_Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

This file was mostly hacked together using information from _[this How-To.](https://help.ubuntu.com/community/RadeonDriver)_ However, you will notice many options and alternate configurations commented out throughout the file. These options were various things I tried to fix the problem as I clicked through the internet looking for solutions. There are two vendorname and modelname values in the "Monitor" section because, previously, when I had Ubuntu 8.04 on the computer, either of those setups enabled the TV to work. Some of the other values were also stolen from the previous xorg.conf file which I saved precisely for this reference. I can post the contents of that file if you would like. The reason I am not using it is because it was configured to run the fglrx drivers for the card and, to my knowledge, those don't exist for the 9600 series anymore. I think that could have been part of the previous problem, but I digress.

Anyways, I was hoping someone with a bit more knowledge at configuring the xorg.conf file could take a look at my current setup and see what I might be missing/configuring wrong. It never hurts to have a second set of eyes. I chose the 800x600 resolution because that was the best resolution I could get on the big screen TV and still have X render correctly when I was running Ubuntu previously. It seems like there is no problem with the drivers or the S-video cable as I can see the boot loading on the TV screen just fine and dandy. It's only when X starts (at the login screen) that the TV fails to show anything. Does anyone have any ideas on what I have misconfigured in my xorg.conf file?

All help is appreciated, and thank you ahead of time for helping me out with this.

Best of luck to everyone.

---

### Post by BJ_Covert_Action on 2010-04-12
24(ish) hour bump.

It looks like the Radeon 9600 proprietary drivers can be found as part of the Catalyst legacy driver package _[here.](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English)_ Does anyone know if these will work with 9.10 at all? I know there were some significant updates to X for that distribution so I don't know if it is still compatible.

Hopefully I can get some input on this. Thanks guys. :)

---

### Post by BJ_Covert_Action on 2010-04-14
Howdy All,

So, I never got a response to this but I did come up with a temporary workaround that will need some tweaking. Essentially, in 9.10 you have to use the xrandr command to tweak your S-video output settings. By running the following two commands, you can force your ati card to output to 800x600 resolution:

```

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600

```

This will allow S-video output temporarily (for this single boot session). However, this configuration will be lost upon reboot. The best workaround I found to this issue was to input the to commands into my */etc/gdm/Init/Default* script. Essentially, this script loads at boot time just before the login prompt (note, scripts like .bashrc not load until after login which could be a problem). Thus, by putting the aforementioned commands into this GDM startup script, the S-video output is enable just before the login screen which will allow it to render prior to logging in (useful if you intend to use the TV as your only monitor).

Also, I found that you can disable the VGA monitor via 

```

xrandr --output VGA-0 --off

```

I am not sure there is a lot of practical purpose to this, but its an option that I also put in my gdm script (though I may well regret that later).

Anyways, I hope this helps anyone who stumbles upon this thread by mistake or in hopes of finding some resources. Chances are I won't be visiting it too often again, so if you have any questions for me, you would do better to shoot me a direct message on my user CP.

Cheers.

---

