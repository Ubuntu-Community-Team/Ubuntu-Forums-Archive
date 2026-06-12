---
title: "GDM Greeter resolution"
date: 2008-08-01
forum: Desktop Environments
---

### Post by aliengoods on 2008-08-01
I've been trying to figure out how to set the resolution in GDM greeter and I haven't come up with anything solid. What I want is 1280x1024. What it gives me is 1280x768. I'm thinking I have to set the config in xorg.conf, or at the very least set xorg.conf to only display the resolution I want. 

Here are a few details:
Ubuntu 8.04 64bit Server
XFCE Installed
A few apps installed, but the only thing that may affect video is VMWare Workstation

Here is my xorg.conf:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

I'm used to dealing with configs more like this:

```
Section "Monitor"
 Identifier "Configured Monitor"
 Vendorname "Sony"
 Modelname "Sony MFM-HT75W (Digital)"
 Horizsync 28.0-64.0
 Vertrefresh 57.0-63.0
  modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
 Gamma 1.0
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device "Configured Video Device"
 Monitor "Configured Monitor"
 Defaultdepth 24
 SubSection "Display"
  Depth 24
  Virtual 1280 1024
  Modes "800x600@60" "1024x768@60" "640x480@60" "1280x768@60" "1280x960@60" "1280x1024@60"
 EndSubSection
EndSection
```

So, being as I don't have a clue what horizontal and vertical sync freqs my monitor is capable of, does anyone know how to get the current settings out of an X session that is running the resolution I want? Or where do the "default" values in my config pull from? Is there an easier way to change my GDM greeter resolution? Please note that right now I'm using a crappy integrated video card with a 10 year old 17 inch CRT.

On a tangential issue, I'm in the market for a 24 inch LCD and a good video card with Svideo out and possibly hdmi out (and of course linux 64-bit compatibility). Can anyone recommend brands/models from either category that they've had good experiences with? I would prefer to keep the video card under $150 and the monitor under $400. Thanks.

---

### Post by Linja on 2008-08-01
You will need to edit the Screen section of your current xorg.conf to look more like the example you posted. Xorg.conf is where GDM gets its ideas, it tries to use the highest value that is specified. In most cases, it works out of the box but sometimes it takes a little coaxing by explicitly listing resolutions.

As for video cards, I would recommend Nvidia 8600 or 9600. I have recently bought a 9600GT 512MB that I am very happy to have. The downside is that I had to install the drivers manually as they were (are?) not in the repositories yet. But it's not all that hard to do. As for the monitor, I bought a new one too: Samsung 2253BW, 22 inch, fast, amazing colours. Looking at the ACER I bought two years ago makes me depressed

---

