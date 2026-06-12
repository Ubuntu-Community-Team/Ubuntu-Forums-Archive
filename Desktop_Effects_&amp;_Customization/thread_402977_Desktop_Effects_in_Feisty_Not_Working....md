---
title: "Desktop Effects in Feisty Not Working..."
date: 2007-04-06
forum: Desktop Effects &amp; Customization
---

### Post by siefer132 on 2007-04-06
Can someone Help me out? When i open my Desktop Effects from the System->Preferences->Desktop Effects, it says "The Composite Extension is not available. 
Here is my Device section in the xorg.conf file

Section "Device"
	Identifier	"ATI RADEON X1400"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option "DRI" "true"
	Option "AGPMode" "8"
	Option "AccelMethod" "XAA"
	Option "XAANoOffscreenPixmaps" "true"
	Option "RenderAccel" "true"
	Option "EnablePageFlip" "true"
	Option "ColorTiling" "true"
EndSection

---

### Post by joeally on 2007-04-08
I have the same problem arghhhh accept with my radeon x1600pro. Beryl does nothing either

somone plz help

Thanks Joe

---

### Post by rezyek on 2007-04-09
same here ...
with an Ati X800pro

---

### Post by igknighted on 2007-04-09
To the first to posters... those cards aren't supported by that driver.  Nothing over x800 gets 3d.  To the third poster, some x800/x850 pci-e cards don't work, is yours pci-e or agp?  Also, did you enable the composite extension at the end of xorg.conf?

[http://help.ubuntu.com/community/RadeonDriver](http://help.ubuntu.com/community/RadeonDriver) is a great resource, use it to set up the driver.  If it doesn't work, you need to go back and use fglrx/XGL.

EDIT: Note that when the driver how-to says ati, most people will want to use "radeon" instead.  From what I have read, "ati" is for rage cards while "radeon" is for radeon cards (which are most ati cards).

EDIT2: The tool you are trying to use is worthless (Desktop Effects).  Don't use it.  If you want AIGLX you need to use the link I provided, as fglrx doesn't support composite (hence the error you see).  It also can't set up XGL, so you have to do that yourself.

---

### Post by joeally on 2007-04-11
Thanks for your help mate I'll see if that works

---

### Post by sirbats on 2007-04-11
> **igknighted said:**
> To the first to posters... those cards aren't supported by that driver.  Nothing over x800 gets 3d.  To the third poster, some x800/x850 pci-e cards don't work, is yours pci-e or agp?  Also, did you enable the composite extension at the end of xorg.conf?

[http://help.ubuntu.com/community/RadeonDriver](http://help.ubuntu.com/community/RadeonDriver) is a great resource, use it to set up the driver.  If it doesn't work, you need to go back and use fglrx/XGL.

EDIT: Note that when the driver how-to says ati, most people will want to use "radeon" instead.  From what I have read, "ati" is for rage cards while "radeon" is for radeon cards (which are most ati cards).

EDIT2: The tool you are trying to use is worthless (Desktop Effects).  Don't use it.  If you want AIGLX you need to use the link I provided, as fglrx doesn't support composite (hence the error you see).  It also can't set up XGL, so you have to do that yourself.

Hi All,

I have ATI RV370 based card in which mentioned on the above link as 3D Experimental "class" but I follow the tutorial and everything went well, beryl installed and 3D destop present :

My card
```

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
01:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]

```

My Device section on xorg.conf
```

Section "Device"
        Identifier        "ATI Technologies Inc RV370 [Sapphire X550 Silent]"
        Driver                "radeon"
        BusID                "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection
#Section "Device"
#	Identifier	" ATI Technologies Inc RV370 [Sapphire X550 Silent]"
#	Driver		"fglrx"
#	BusID		"PCI:1:0:0"
#	Option		"UseFBDev"		"true"
#       Option          "XAANoOffscreenPixmaps"
#EndSection

```
my server lay-out at xorg.conf
```

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier        "Default Layout"
        Screen                "Default Screen"
        InputDevice        "Generic Keyboard"
        InputDevice        "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        
EndSection

#Section "ServerLayout"
#	Identifier	"Default Layout"
#       Option          "AIGLX"         "true"
#	Screen		"Default Screen"
#	InputDevice	"Generic Keyboard"
#	InputDevice	"Configured Mouse"
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
#EndSection

```
commented part is configuration before 3D and uncommented is configuration with 3D work.

I suggest to follow above tutorial for configuring "radeon" card and confirmed open-source driver is better than propetiary one.

thanks
sir Bats

---

