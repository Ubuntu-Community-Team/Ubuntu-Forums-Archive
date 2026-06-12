---
title: "X Windows stuck at 640x480 on SiS 5597/5598 chipset"
date: 2005-06-01
forum: Desktop Environments
---

### Post by Chris_J_W on 2005-06-01
Hi, I've recently set up a Ubuntu (Hoary) system for my mum running XFCE.  I'm having a slight issue getting the resolution to anything above 640x480 though.  ](*,) 

The monitor is an Olivetti DSM 27-615, and the graphics card is an onboard SiS 5597/5598 chipset built onto the motherboard.  It's a relatively old system. 

My problem is that I'm sure I've got xorg.conf set up correctly, so I may be using the wrong driver - I don't know, but it's not working either way.  I know that the hardware is capable of at least 1024x768 at a decent refresh rate as I've used it for that before.

Here's my xorg.conf file.

```

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
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier      "Generic Mouse"
        Driver          "mouse"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/ttyS0"
        Option          "Protocol"              "Auto"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:20:0"
        VideoRam        65536
        Option          "UseFBDev"              "true"
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-62
        VertRefresh     48-100
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Generic Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

When I run startxfce4 with that as the xorg.conf, it starts up at 640x480 with a refresh rate of 86Hz.  Looking in the Xorg.0.log file, I see the following that may be related:

```

...
(II) VESA(0): Total Memory: 16 64KB banks (1024kB)
(II) VESA(0): Generic Monitor: Using hsync range of 30.00-62.00 kHz
(II) VESA(0): Generic Monitor: Using vrefresh range of 48.00-100.00 Hz
(II) VESA(0): Not using mode "1024x768" (no mode of this name)
(II) VESA(0): Not using mode "800x600" (no mode of this name)
(--) VESA(0): Virtual size is 640x480 (pitch 640)
(**) VESA(0): *Built-in mode "640x480"

...

```

Also in that log file, there is no mention of a 1024x768 mode with 16 or 24bpp.  Am I trying to use the wrong driver?  Running "dpkg-reconfugure xserver-xorg" gives a whole heap of possible ones to try from.  I've tried a few, but with much the same results.

Any help ASAP would be fantastic! Thanks heaps!

Chris :cool:

---

### Post by thrift on 2005-06-01
Are you sure the 

VertRefresh 
and
HorizSync 

lines in your xorg.conf have the correct ranges for your monitor?  That would cause the results your describing.  You can probably get the correct numbers from the back of your monitor, the monitor manual, searching inside the windows driver inf file, or hunting on google.

---

### Post by Chris_J_W on 2005-06-01
Yes I'm sure these are the right values.  It's an old second hand monitor, and I can only find it in one place looking on google, but it matches that...

---

### Post by thrift on 2005-06-01
hmm

perhaps there is a more specific driver.  You are using VESA at the moment, which is probably not ideal.  There is an sis driver.

for a full listing of drivers do:

ls /usr/X11R6/lib/modules/drivers/

just strip the _drv.o off the drivername when you use it in xorg.conf

you can use man to see specifics for each driver.

man sis

---

### Post by psychicdragon on 2005-06-01
I'm pretty sure you can only use 640x480 resolution because you're using the the vesa driver.

Try changing this:
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:20:0"
        VideoRam        65536
        Option          "UseFBDev"              "true"
```
To this:
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "sis"
        BusID           "PCI:0:20:0"
        VideoRam        65536
        Option          "UseFBDev"              "true"
```
That's probably all that's required.

---

### Post by Chris_J_W on 2005-06-01
Thanks for the help - I've found a site with a more upto date sis driver, so I'm going to give that a go tonight, and will post results here later depending on the outcome.  I'm pretty sure that it is driver related, but when I tried the sis driver that came with Ubuntu, I got much the same results.  Anyway, will try again tonight.  :cool:

---

### Post by psychicdragon on 2005-06-01
try commenting out the line
```
Option          "UseFBDev"              "true"
```
I'm not even sure what that does, it's not in my config.

---

