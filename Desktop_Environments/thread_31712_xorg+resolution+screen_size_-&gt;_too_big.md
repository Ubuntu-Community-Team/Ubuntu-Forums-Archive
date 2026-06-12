---
title: "xorg+resolution+screen size -&gt; too big"
date: 2005-05-04
forum: Desktop Environments
---

### Post by prem_mallappa on 2005-05-04
Hi,

I just upgraded to hoary, to transform from XF86Config-4 to xorg.conf
i had a screen resolution of 1152x864 bpp 16 working fine with Debian XFree86.
Ubunut's xorg takes the resolution but my screen is bigger than that of my monitor,

my taks bar, main panel are out of  my visible screen size but when i move the mouse to the bottom of desktop the whole desktop moves up and the panels are visible.

Strange xorg.. strange Hoary..

anybody with the same problem

---

### Post by tread on 2005-05-04
You would need to post the config file here I think, but as a quick guess, what it will need is a modelines line. 

[xtiming modeline generator](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---

### Post by alastair on 2005-05-04
Post the xorg.conf.

It sounds like you have "virtual" set i.e. a virtual desktop larger than the physical.

---

### Post by prem_mallappa on 2005-05-05
Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
#       Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
EndSection
Section "InputDevice"
        Identifier      "Generic Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        #Option         "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "no"
        Option          "ZAxisMapping" "4 5"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        8192
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        ModelName    "DDCPROBED"
        DisplaySize  350        250
        #DisplaySize  310        230
        Option          "DPMS"
        HorizSync       30-71
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1152x864" "1024x768"

        EndSubSection
        SubSection "Display"
                Depth           24
                Modes          "1024x768" "1152x864" 
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0  "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Generic Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection


P.S: The display size is added later and now currenly able to  use it with 1024x768 resolution

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=prem_mallappa]
        SubSection "Display"
                Depth           24
                Modes          "1024x768" "1152x864" 
        EndSubSection
EndSection
[/QUOTE]
It seems that since 1024x768 goes first, this is the resolution actually used by Xserver. 
But since you also have 1152x864 in the list, it creates "virtual" screen of size 1152x864 and then only shows the  1024x768 corner of it. 

So if you want to have  1152x864, make it first in the list: 
                Modes         "1152x864"  "1024x768" 

Let me know if it works.

---

### Post by ustas on 2005-05-06
[QUOTE=Alexander Kirillov]It seems that since 1024x768 goes first, this is the resolution actually used by Xserver. 
But since you also have 1152x864 in the list, it creates "virtual" screen of size 1152x864 and then only shows the  1024x768 corner of it. 

So if you want to have  1152x864, make it first in the list: 
                Modes         "1152x864"  "1024x768" 

Let me know if it works.[/QUOTE]

Same shit. In my xorg.conf the onlyest resolution is 1152x864. Here is my xorg.conf in attach.

What have I tryed:

dpkg-reconfigure xorg-server and tryed to reconfigure all my hardware 
tryed to fix it as it was advised on different forums - to use gtf and to add then the given data to my xorg.conf ... nothing helps :-(

I have the same I845 chipset with the build-in video card which share it's video RAM with coputer's RAM.

Also i attached my Xorg.0.log. May be it will helps.


Thx anyway.

---

### Post by prem_mallappa on 2005-05-06
======================================================
Originally Posted by Alexander Kirillov
It seems that since 1024x768 goes first, this is the resolution actually used by Xserver.
But since you also have 1152x864 in the list, it creates "virtual" screen of size 1152x864 and then only shows the 1024x768 corner of it.

So if you want to have 1152x864, make it first in the list:
Modes "1152x864" "1024x768"

Let me know if it works.
======================================================

This is not true since i have edited the file and let only 1152x864 in the line but no success...  SHIT xorg sucks!!!

---

### Post by kb00heda on 2005-05-07
Alexander:

I had a similar kind of "picture-in-picture" situation, with a bigger virtual desktop (1280x1024), and a smaller physical one (800x600). My mode line was indeed

SubSection "Display"
		Depth		24
		Modes		"800x600" "1280x1024"
EndSubSection

but when I removed the latter resolution

SubSection "Display"
		Depth		24
		Modes		"800x600"
EndSubSection

it worked perfect, i.e., I really got 800x600 only.

Thank you for the tip!  :)

---

