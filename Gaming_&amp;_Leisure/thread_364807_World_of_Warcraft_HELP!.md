---
title: "World of Warcraft HELP!"
date: 2007-02-18
forum: Gaming &amp; Leisure
---

### Post by denverreynolds on 2007-02-18
I installed Wine and Wow per the instructions in these forums. My PC is a Dell Inspiron with an X1400 ATI video card duel core CPU. I can load up, log in and change realms. When I try to enter the game the computer locks up. Here is my wtf.conf file:

SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "32"
SET farclip "477"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET realmList "us.logon.worldofwarcraft.com"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET gxMultisampleQuality "0.000000"
SET expansionMovie "0"
SET readEULA "1"
SET realmName "Proudmoore"
SET gameTip "14"
SET gxWindow "1"
SET gxMaximize "1"
SET gxCursor "0"
SET Gamma "1.000000"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET checkAddonVersion "0"
SET gxApi "OpenGL"
SET UIFaster "2"
SET ffxGlow "0"
SET shadowLevel "0"
SET gxFixLag "0"
SET anisotropic "16"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET mouseSpeed "1"



Here is my xorg.conf:

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


When I check glxinfo | grep render, I get:
GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: ATI Mobility Radeon X1400 Generic

I really want to stay with Linux but I need my Warcraft to work. PLEASE HELP ME!!!!

---

### Post by justin whitaker on 2007-02-18
I do not know much about ATI configuration, but this block has me puzzled:

Section "Device"
Identifier "ATI Technologies, Inc. ATI Default Card"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

Shouldn't that driver line=ati? 

BTW, stick with it. I have WoW running under Crossover on an NVIDIA card. You can play WoW on Linux.

---

### Post by Sammi on 2007-02-19
I'm no expert on xorg.conf, but your xorg.cong file seems to have a lot of double entries. As I understand it one of these two sections has to go:

```
Section "Device"
    Identifier  "ATI Technologies, Inc. ATI Default Card"
    Driver      "vesa"
    BusID       "PCI:1:0:0"
EndSection
``````
Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"
EndSection
```I would delete the first one. Remember to backup your xorg.conf before editing it though!

For reference:
 * fglrx is the proprietary closed-source binary driver from ATI
 * ati is the open source driver for ATI cards
 * vesa is a generic open source driver, with little or no 3d functionality

ATI card users have a lot of problems, as ATI haven't done a good job of the Linux drivers unfortunately, unlike Nvidia who's drivers are pretty good. That's also why we have open source drivers for ATI, while the open source drivers for Nvidia are only now getting started.

But I heard that this is actually a common problem you're expariencing. Here are two treads where it's discussed:
[http://ubuntuforums.org/showthread.php?t=156841](http://ubuntuforums.org/showthread.php?t=156841) post #8
[http://www.ubuntuforums.org/showthread.php?t=363390](http://www.ubuntuforums.org/showthread.php?t=363390) post #5

Apparantly all you need to do is to append these three lines to the device section of your xorg.conf file:
        ```
Option "Capabilities" "0x00000800"
Option "UseFastTLS" "off"
Option "KernelModuleParm" "locked-userpages=0"
```So it should look like this:
```
section "Device"
Identifier  "aticonfig-Device[0]"
Driver      "fglrx"
Option "Capabilities" "0x00000800"
Option "UseFastTLS" "off"
Option "KernelModuleParm" "locked-userpages=0"
EndSection
```You can also just create a new xorg.conf from scratch by doing the command and following the onscreen directions: ```
sudo dpkg-reconfigure xserver-xorg
```It should be noobfriendly enough

---

