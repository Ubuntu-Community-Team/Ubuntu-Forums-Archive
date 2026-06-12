---
title: "Increasing screen resolution"
date: 2006-07-27
forum: Desktop Environments
---

### Post by apastuszak on 2006-07-27
I have a Sony CRT monitor (I think it's a GX440), that is currently running at 1280x1024.  The monitor supports up to 1600x1200, but the highest resolution choice Ubuntu gives me is 1280x1024.  What can I do to increase the resolution on the monitor so I can get up to 1600x1200?

Andy

---

### Post by autocrosser on 2006-07-27
Well-I'm at work right now so I can't be exact, but you will need to modify your xorg.conf. I get the monitor specs for size (mm,mm)--vertical & horizontal numbers & then include a modeline that has the resolutions you want to use.
 
I'm sure that some will post before I get off work, but I'll check back & lend a hand if not----

---

### Post by autocrosser on 2006-07-27
Ok--Some snips from my xorg.conf---

First, The Device section--

Section "Device"
    Identifier  "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver      "nvidia"
        BusID       "PCI:1:0:0"
        Option      "TwinView"                  "true"
        Option      "MetaModes"     "1280x1024,1280x1024;1280x1024,NULL;1024x768,1024x768;800x600,800x600"
        Option      "TwinViewOrientation"       "RightOf"
        Option      "NoLogo"                    "true"
        Option      "RenderAccel"               "true"
        Option      "CursorShadow"              "true"
        Option      "Backingstore"              "true"
        Option      "RandRRotation"             "true"
        Option      "Coolbits"                  "true"
        #Option      "NoPowerConnectorCheck"     "true"
        #Option      "ConnectedMonitor"          "dfp, crt"
        Option      "AllowGLXWithComposite"     "true" 

EndSection

I run dual monitors--so the main thing you need to look at is the "MetaModes" option

Next--describe your monitor--

Section "Monitor"
        DisplaySize     376.32  301.056
        Identifier    "Monitor0"
        ModelName       "VL1918"
        VendorName      "Princeton"
        HorizSync       31.0 - 79.0
        VertRefresh     60.0 - 70.0
    Option        "DPMS"
EndSection

Note that the DisplaySize in is MM & NOT in quotes--

Last--Define your Screen--

Section "Screen"
        Identifier  "Screen0"
        Device      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor     "Monitor0"
        DefaultDepth 24
        Subsection "Display"
            Depth       24
            Modes       "1280x1024" "1024x768" "800x600" 
        EndSubsection
    EndSection

I don't use all the other color depths, so why have them??

In your case--a single monitor MetaModes & Modes should agree like:

"1600x1200" "1280x1024" "1024x768" & so on---

Make sure you backup your /etc/xorg.conf first---

sudo gedit /etc/xorg.conf

rename the file to something like xorg.conf-old

then edit the file--be careful & recheck your work--stuff not in the "proper" format will cause a Xorg non-start:!:

When you are done save the file & either reboot or log-out & control-alt-delete--

---

### Post by Jhongy on 2006-07-27
If you haven't customised your xorg.conf, then you can type:

```
sudo dpkg-reconfigure xserver-xorg
```

You will be presented with lots of questions - just accepting the defaults for most of them should be fine.

When you get to the question about graphics drivers, select yours from the list.

When you get to the question about resolutions, you can scroll down the list and select the one(s) you want to be available with the spacebar.

Answer all the rest of the questions, and when it prompts you if you want to write out a new xorg.conf, choose yes. When you're done, restart the computer. The resolutions you selected should then be selectable.


If there are any problems, the configuration tool should have automatically created a backup of your old xorg.conf in the /etc/X11 directory.

You may still need to install your graphics driver.

---

### Post by Skia_42 on 2006-07-28
if that doesn't work, you can manually edit your xorg.conf by opening it with Gedit using this command:> sudo gedit /etc/X11/xorg.confThis is the place that you want to edit, it's from my file:> Section "Monitor"
	Identifier	"iMac"
	HorizSync	30-112
	VertRefresh	50-160
	Option		"DPMS"
	ModeLine	**"1280x960"** 122.25 1280 1344 1440 1696 960 965 968 1002 +hsync +vsync -csync
EndSection


---

