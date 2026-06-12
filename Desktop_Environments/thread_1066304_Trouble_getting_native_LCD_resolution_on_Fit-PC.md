---
title: "Trouble getting native LCD resolution on Fit-PC"
date: 2009-02-10
forum: Desktop Environments
---

### Post by Child of Wonder on 2009-02-10
I have a Fit-PC v. 1.0 that I've put in the kitchen and connected to our Westinghouse LTV-19w6 TV via VGA.  The TV's native res is 1440x900.  The Fit-PC uses an AMD Geode platform and the only resolution I can get out of it is 800x600 (safe mode).

I've tried creating custom modelines for 1440x900 but no good.  Fit-PC forums are of little help.  The Geode CAN do widescreen as others have reported 1680x1050 resolutions.

I have the xserver-xorg-driver-geode package installed.  

Any ideas?

Here is my xorg.conf file.

> Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
EndSection

Section "Module"
        Load "xtrap"
        Load "extmod"
        Load "dbe"
        Load "dri"
        Load "glx"
        Load "record"
        Load "freetype"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "geode"
        BusId           "PCI:0:1:1"
        BoardName       "Geode LX Video"
        VendorName      "Advanced Micro Devices [AMD]"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       20 - 90
        VertRefresh     50 - 75
        UseModes    "Custom"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        DefaultDepth    16
        SubSection "Display"
                Viewport 0 0
                Depth    16
                Modes    "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "Modes"
   Identifier "Custom"
   Modeline "1440x900"  108.84 1440 1472 1880 1912 900 918 927 946
#   Option   "DPMS"
EndSection

Relevant log entry shows:

> (II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) GEODE(0): Primary V_BIOS segment is: 0xc000
(EE) GEODE(0): GPIO pins are in serial mode.  Assuming no DDC
(II) GEODE(0): Configured Monitor: Using hsync range of 20.00-90.00 kHz
(II) GEODE(0): Configured Monitor: Using vrefresh range of 50.00-75.00 Hz
(II) GEODE(0): Clock range:  25.18 to 229.50 MHz
(II) GEODE(0): Not using mode "1440x900" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "640x350" (unknown reason)
(II) GEODE(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "640x400" (unknown reason)
(II) GEODE(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "720x400" (unknown reason)
(II) GEODE(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "640x480" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "640x480" (unknown reason)
(II) GEODE(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "640x480" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "640x480" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "800x600" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "800x600" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "800x600" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "800x600" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "800x600" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1024x768" (unknown reason)
(II) GEODE(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "832x624" (unknown reason)
(II) GEODE(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1360x768" (unknown reason)
(II) GEODE(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1360x768" (unknown reason)
(II) GEODE(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1920x1080" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) GEODE(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) GEODE(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(WW) GEODE(0): Mode pool is empty
(EE) GEODE(0): No valid modes were found
(II) UnloadModule: "geode"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by Hobgoblin on 2009-02-10
You could try 
```
Option "UseEDID" "FALSE"
```
in the monitor section.

---

### Post by Child of Wonder on 2009-02-10
I found the problem.  The Fit-PC BIOS was still set to use 2MB video memory back when I was using it as an IPCop router.

I increased the video memory to 16MB and now it displays 1440x900 fine.

Thanks!

---

