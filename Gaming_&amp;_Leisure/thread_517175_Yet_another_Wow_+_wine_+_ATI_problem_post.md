---
title: "Yet another Wow + wine + ATI problem post"
date: 2007-08-04
forum: Gaming &amp; Leisure
---

### Post by pyrodrake on 2007-08-04
OK, so I tried to figure this out on my own using various tutorials I've found online, and reading MANY different forum posts, but I can't seem to find a resolution to the exact problem I'm having, so I'm sorry if this is a repost.

I have an AMD64 4200+ with an ATI X300 graphics card (yeah, I know, I couldn't afford an nVidia when this computer was built, otherwise I'd switch in a heartbeat).  I was able to play WoW somewhat OK using the fglrx drivers for ATI (I may have gotten it to run better, but had other things I had to mess with first), but had other problems in KDE trying to get dual monitors and compiz/beryl running properly.  I switched to the open source drivers and absolutely love the dual head support, and many other things just run a hell of a lot more smooth.  But now, when I try to load up WoW, it starts up, but has a lot of video issues:

1) It trys to run "full screen" using a resolution of 2560x1024, but only on one monitor, so it scrunches down in the center of the screen.

2) If I try to edit the config.wtf file back to 1280x1024 and try to re-load WoW, it automatically changes it back to 2560x1024

3) It refreshes the screen once every 30-40 seconds (making it very hard to exit the game)

4) It just looks bad (eg: coloring is off, everything looks half-rendered [like the top half of the portal doesn't load], and the portions that do load get pixelated and have lines through them.

5) If I switch it to run in windowed mode and at a resolution of, lets say, 800x600, I still suffer from issues 3 & 4 (but at least it remembers/keeps my resolution settings

I am at a loss at this point.  I really don't want to switch back to the fglrx drivers (especially after all the problems I've read about them in other posts, and the problems I've had in KDE with them), but honestly I'm tired of booting into Windows.  This would be the last program I need to get running to prevent me from ever having to boot into Windows on a near-daily basis...

Here is my /wow/config.wtf:

```
SET gxApi "opengl"
SET gxWindow "1"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET farclip "477"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET Gamma "1.000000"
SET MusicVolume "0"
SET SoundVolume "1"
SET MasterVolume "0.90000003576279"
SET realmName "Twisting Nether"
SET gameTip "72"
SET AmbienceVolume "0.40000000596046"
SET uiScale "1"
SET mouseSpeed "1"
SET profanityFilter "0"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET UberTooltips "0"
SET ShowTargetCastbar "1"
SET UnitNameNPC "1"
SET autoSelfCast "1"
SET cameraView "0"
SET EnableMusic "0"
SET readScanning "-1"
SET readContest "-1"
SET ShowVKeyCastbar "1"
SET guildMemberNotify "1"
SET patchlist "us.version.worldofwarcraft.com"
SET checkAddonVersion "0"
SET minimapInsideZoom "2"
SET showToolsUI "1"
SET spellEffectLevel "1"
SET weatherDensity "0"
SET gxDepthBits "24"
SET baseMip "1"
SET ffxDeath "0"
SET ffxGlow "0"
SET shadowLOD "0"
SET accountName "anathem"
SET lastCharacterIndex "2"
SET minimapZoom "4"

```

And my xorg.conf file:
```
Section "ServerLayout"
	Option		"AIGLX"		"true"
	Identifier    	"Default Layout"
	Screen         	"Screen1" 0 0
	InputDevice    	"Generic Keyboard"
	InputDevice    	"Configured Mouse"
EndSection

Section "Files"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
	Load  "GLcore"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Buttons"	"9"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	HorizSync	28-72
	VertRefresh	43-60
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  	"Output1"
	BoardName	"ATI Radeon X300"
	Screen 0
	VendorName	"ATI"
	Driver		"radeon"
	Option		"XAANoOffscreenPixmaps"
	Option		"AGPMode"	"8"
	Option		"ColorTiling"	"on"
	Option		"AccelDFS"	"true"
	Option		"TripleBuffer"	"true"
	Option		"MonitorLayout"		"LCD, CRT"
	Option		"CRT2Position"		"LeftOf"
	Option		"MetaModes"	"1280x1024-1280x1024"
	Option		"MergedXinerama"	"on"
	Option		"MergedNonRectangular"	"true"
	Option		"MergedFB"		"true"
      Option 		"AGPFastWrite" "true"
      Option 		"DisableGLXRootClipping" "true"
      Option 		"AddARGBGLXVisuals" "true"
      Option 		"AllowGLXWithComposite" "true"
      Option		"EnablePageFlip" "true"
	BusID       	"PCI:7:0:0"
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Output1"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

I am running Kubuntu (although that really shouldn't make much difference) and the 64 bit version.

Here's what I've tried so far:
Set various screen resolutions and refresh rates in WoW
Change from full screen to windowed mode and vica versa
Tried both OpenGL and Direct3D (which WoW REALLY doesn't like d3d at all)
Change the Driver in my Device section of my xorg.conf file to "radeon" to "ati" and back again
Able to run glxgears without any problem and also anything else that tests the driver installation comes out fine (can't think of specifics ATM, too tired)
Tried Ubuntu 32 AND 64 and Kubuntu 32 (which is why I don't think KDE is the issue)
Verified all WoW files are there using the repair utility
Copied the 4 Windows DLL's to my windows/system32 directory (MSVCP60.DLL, MFC42.DLL, RICHED20.DLL, RICHED32.DLL)
Followed all the steps in the Troubleshooting section of: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
All failed/no results  :(

Any help anyone can provide would be greatly appreciated!  Thanks in advance.

EDIT: Oh, and I am not running Beryl (can't anyway with this graphics card and dual head set up) or Compiz at the moment either

---

### Post by cor2y on 2007-08-04
At present with ATI cards you can't have your cake and eat it as well.
Meaning you have to make a choice.
Open Source drivers = compiz/beryl/compizfusion, dual monitor support but no good 3d gaming support.
fglrx drivers = equal good 3d gaming support but no eye candy.and just about everything else.
Sure there is XGL if you want eye canday and 3d gaming but you can never tell what the result will be until you install and fire up XGL, it doesn't always work.

My advice first install the official ATI drivers via synaptic.
See what happens.
If you miss the eye candy then try the XGL profile, the guide for doing that is located in the guide section.

---

### Post by pyrodrake on 2007-08-04
I almost figured the answer was going to be something along those lines, but I figured I'd ask anyway.  :-D
Welp, its not so much the eye candy I like, so much as the need for full dual head support...  I'll try XGL and let you know it works out.
Thanks for your help.

---

### Post by pyrodrake on 2007-08-06
OK, so I think I figured out a solution to my problem.  It's probably a work around that took me more time than it was actually worth, but none-the-less, it worked...  ;)  I created another 5GB partition elsewhere on my hard drive and reinstalled Kubuntu on it, and have just what I need to get WoW running with OpenGL and the FGLRX drivers.  I still have to reboot my system to get to the other install of Kubuntu, but at least it works now...  :D

My only other questions would be this:

1) There is probably an easier way to set up multiple instances of X (using basically a different xorg.conf with each instance) with one install of Kubuntu.  If someone can offer any suggestions as to how, I'm all ears.  :)

2) In WoW itself, is there anyway I can enable the Hardware Mouse option?  Using it as software is causing my mouse to lag at times and it doesn't move as smoothly on the screen.

Thanks again.

---

