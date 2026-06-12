---
title: "Help! Cannot change X11 resolution!"
date: 2016-02-08
forum: Desktop Environments
---

### Post by the kaz on 2016-02-08
Hi out there,
my Lubuntu 14.04 installation (fluxbox) is driving me mad. I need to change the resolution details for 1024x768, but no matter what I do, the system just ignores me. :-(

I need to activate this ModeLine to run my display without errors:

```
ModeLine "needthis" 60.000 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
```

(and yes, I tried about a dozen different names of this ModeLine, including "1024x768_60"...)

First, I wanted to do this via xrandr, but after --newmode and --addmode", the mode is listed but cannot be activated. 

```
xrandr --output default --mode "needthis" --rate 60
```
results in 
```
xrandr: Failed to get size of gamma for output default
```

if I add 

```
--gamma 1:1:1
```

I get 

```
xrandr: size of gamma is zero
```

In both cases, the system just continues to use the old resolution. 

Then, I tried to add a modeline to that effect to my xorg.conf. I now have added that d*mn ModeLine to just about every block there is in my xorg.conf, just to be sure. But in the log, it always says: 

```
Not using mode "needthis" (no mode of this name)
```

and sure enough the mode is ignored. 

I'm banging my head against the wall here. Why does something a basic as this just not work? I cannot change to any other resolution (e.g. "800x600"), either, by the way. :-((

Here is my xorg.conf (which looks totally stupid now, I know): 

```

Section "Modes"
        Identifier "all0"
        ModeLine "needthis" 60.000 1024 1048 1184 1344 768 771 777 806 -HSync -VSync
EndSection

Section "Monitor"
        Identifier "disp0"
        Option "DDC" "False"
        ModeLine "needthis" 60.000 1024 1048 1184 1344 768 771 777 806 -HSync -VSync
        Option "Preferred Mode" "needthis"
EndSection
Section "Device"
        Identifier "card0"
        Driver "vesa"
EndSection

Section "Screen"
        Monitor "disp0"
        Identifier "default"
        SubSection "Display"
                Modes   "needthis"
        EndSubSection
EndSection

```

Can anyone help me?

Thanks in advance.

---

### Post by vasa1 on 2016-02-08
> **the kaz said:**
> Hi out there,
my Lubuntu 14.04 installation (fluxbox) is driving me mad. ...
How does the standard Lubuntu with Openbox work?

---

### Post by the kaz on 2016-02-08
I will try that tomorrow. Could that make a difference, though? The xorg server should be the same. 

I will try Lubuntu from USB stick tomorrow, and'll throw in Knoppix for good measure. If anyone has any pointer as to what might go wrong, please feel free to drop me a line. I cannot believe that something so simple could not work with the plain vesa driver (on an Atom D2xxx), so it must be me doing something wrong. 8-(

---

### Post by anglican on 2016-02-12
Have you tried using cvt to generate the modeline, e.g.

cvt 1280 1024

The modeline goes in the Monitor section and the mode in the Screen section. Something like:

Section "Monitor"
...
Modeline "1280x1024_60.00"  109.00  1280  1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
...
EndSection

Section "Screen"
...
    SubSection "Display"
        Depth    24
        Modes    "1280x1024" "1024x768"
    EndSubSection
EndSection

---

