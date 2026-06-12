---
title: "Unable to set 1280*1024 screen resolution in Dell Laptop"
date: 2009-05-30
forum: Desktop Environments
---

### Post by truth_seeker_3535 on 2009-05-30
Dear Pro's 

I installed ubuntu 9.04 on new Dell Inspiron 1525 Laptop. But the resolution is not good... it is now 1280*800(16:10) and this is the maximum resolution which is available in the "preference-->display".

How can i set it to 1280*1024?

the following is the xorg.conf

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by ajgreeny on 2009-05-30
You could try editing your /etc/X11/xorg.conf file and adding the relevant resolution you want in the following format.  Note I also have the screen refresh rates added, but you may not need those.
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```
Just add any of your own figures where mine are and you may be lucky and get what you want.

---

### Post by asmoore82 on 2009-05-30
according to a quick google for "Dell Inspiron 1525 Laptop;"
it is a Widescreen laptop, 1280x1024 is not a Widescreen resolution.

to see what is auto-detected as even possible, pop open a terminal and:
```
xrandr
```

my lenovo T61 goes no higher than 1280x800, looks like this:
```
**xrandr**
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       60.0*+   50.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS-1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by kerry_s on 2009-05-30
make sure you set the right:
```
	HorizSync 	31-81
	VertRefresh 	56-75
```

for your monitor.

mine:

---

### Post by truth_seeker_3535 on 2009-05-31
Thanks for the quick replies...

ok... its nice information that my laptop will not support 1280*1024. But my current resolution 1280*800 gives me VERY DARK BOLD colour for my evolution new mails, gmail login screen, etc, which doesnt look good at all. So i blieve there should be one more level up for my screen resolution (my hard guess) but which is not showing in the preference-display ( i had seen in some systems, that the supported highere resolutions are not listed in the graphics display tool)

the following is my xrandr output...

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)


from this i think, my maximum resolution is 1280*1280 (am i right?) . if so how can i set it to that resolution.

---

### Post by kerry_s on 2009-05-31
a quick google tells me your max resolution is 1280x800.
[http://shopping.msn.com/specs/inspiron-1525-notebook/itemid1137743362/?itemtext=itemname:inspiron-1525-notebook](http://shopping.msn.com/specs/inspiron-1525-notebook/itemid1137743362/?itemtext=itemname:inspiron-1525-notebook)

if the fonts are bold, your dpi needs to be adjusted in the font settings.

your video card can do up to 1280 x 1280, but your internal screen can not.
you can go virtual up to 1280x1280, but that would mean pushing your screen around. if you want to try that:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
               Virtual       1280 1280
		Modes	"1280x800"	
	EndSubSection
EndSection
```

---

### Post by asmoore82 on 2009-05-31
> **kerry_s said:**
> a quick google tells me your max resolution is 1280x800.
[http://shopping.msn.com/specs/inspiron-1525-notebook/itemid1137743362/?itemtext=itemname:inspiron-1525-notebook](http://shopping.msn.com/specs/inspiron-1525-notebook/itemid1137743362/?itemtext=itemname:inspiron-1525-notebook)

if the fonts are bold, your dpi needs to be adjusted in the font settings.

your video card can do up to 1280 x 1280, but your internal screen can not.
you can go virtual up to 1280x1280, but that would mean pushing your screen around. if you want to try that:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
               Virtual       1280 1280
		Modes	"1280x800"	
	EndSubSection
EndSection
```

Editing xorg.conf is no longer required for that either...
the above effect can be achieved "on-the-fly" with this:
```
xrandr --fb 1280x1280 --output LVDS --mode 1280x800 --panning 1280x1280
```

for the "VERY DARK BOLD" color problem, you may need to adjust advanced font properties
at "System -> Preferences -> Appearance" and the "Fonts" Tab

---

