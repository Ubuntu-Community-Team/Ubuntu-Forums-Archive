---
title: "Windows and buttons too large"
date: 2019-11-10
forum: Desktop Environments
---

### Post by dam034 on 2019-11-10
Dear users,

I have a PC with ubuntu 18.04 that I carry with me to work.

When I connect it to a 42'' tv via hdmi cable, the VLC software displays windows and buttons too large, as shown in these screenshots:
[ATTACH=CONFIG]284382[/ATTACH]
[ATTACH=CONFIG]284381[/ATTACH]
So I went in monitor settings and I see a 7'' monitor:
[ATTACH=CONFIG]284380[/ATTACH]
But the PC is connected to a 42'' monitor.

At the moment, only VLC gives me this problem. And only connected to this monitor, because if I connect to other monitors, it works.

How can I fix this issue?

Thanks

---

### Post by Autodave on 2019-11-10
Have you tried a different cable on the monitor that reports as a 7"?

---

### Post by dam034 on 2019-11-11
In the PC I also have windows 10, and it reports a 42'' tv, and its name.

So, if Win 10 works, the problem is always the cable or ubuntu?

Thanks

---

### Post by Holger_Gehrke on 2019-11-11
It could be the cable because there's a backchannel from the Display to the PC built into the connection on all modern display. It's called DDC (Display Data Channel) and is used among other things for transmitting EDID (Extended Display Information Data) which tells the PC the resolutions the Display is capable of supporting, the preferred (native) resolution, the physical dimensions of the display and lots of other details. 

So there's three possibilities: 
[LIST]
[*]The cable is defective and doesn't have the pins for DDC (might be broken or it's some cheap cable that doesn't have those pins, those work with windows IF you install a 'driver' for the display (which actually is just a text file giving the information that should be reported as EDID) 
[*]The cable is fine and the EDID the display sends is bogus (more likely than you'd think for TVs, because normal consumer electronics devices don't care about EDID and just use whatever they think is standard; also TVs in standby often don't transmit EDID; TVs with multiple connector and set to use a specific one don't send EDID to the ones not in use; and of course there's also the possibility of the memory storing the EDID in the display having gone bad leading to the data and the checksum of it not agreeing) 
[*]Some contact in the interface has come loose if the cable is removed and attached often enough 
[/LIST]
 
There are tools for getting EDID and translating it to something human-readable in the package read-edid. If the command ```
sudo get-edid|parse-edid
``` in a terminal doesn't find a DDC among the various i²c buses in your computer, than the cable is defective (or you've got a bad contact). If it does find a DDC but the information it gets and prints from it is bogus, then the display is 'lying' about what it is and can do. There are ways to pass EDID in a file to the graphics driver as a kernel parameter, but that's not a good fit for this situation because AFAIK it's meant for a situation where the display giving no or wrong EDID is the only one that ever gets connected to the respective port.

Holger

---

### Post by dam034 on 2019-11-12
So, I went to win 10 to see, and I can see this:
[ATTACH=CONFIG]284394[/ATTACH]
So only the brand.

I also executed the commands you wrote:
```
root@pcgame:~# get-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 5
No EDID on bus 6
No EDID on bus 7
No EDID on bus 8
No EDID on bus 9
No EDID on bus 11
2 potential busses found: 0 10
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
Bus 0 doesn't really have an EDID...
256-byte EDID successfully retrieved from i2c bus 10
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;m&#65533;	x
&#58467;TL&#65533;&PTqO&#65533;&#65533;:&#65533;q8-@X,E&#65533;ZrQ&#65533; n(U&#65533;Z&#65533;:>S
      &#65533;LG TV
Looks like i2c was successful. Have a good day.
       &#65533;&&#65533;N&#65533; !"&P	Wg
                                   &#65533;-&#65533;&#65533;q X,%&#65533;Z&#65533;&#65533;Q&#65533;
                                                             @&#65533;5&#65533;Z:&#65533;q8-@X,E&#65533;Zroot@pcgame:~# parse-edid
^C
root@pcgame:~# 
```

So have I to change the hdmi cable?

Thanks

---

### Post by Holger_Gehrke on 2019-11-13
You only ran the first half of the command. 'get-edid' finds the DDC and if there's EDID to be found outputs it as found - which means in some unreadable to humans binary format - to standard output. By sending that output through a pipe to 'parse-edid' you get something human-readable. The only readable information in the output you posted is 'LG TV', which seems like it is the same thing Windows tells you about the device. There should be more, way more information (output for the external display connected to my system to give you an idea):
```

$ get-edid |parse-edid 
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 5
No EDID on bus 6
No EDID on bus 7
No EDID on bus 8
1 potential busses found: 1
256-byte EDID successfully retrieved from i2c bus 1
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
    Identifier "BenQ GW2270"
    ModelName "BenQ GW2270"
    VendorName "BNQ"
    # Monitor Manufactured week 50 of 2017
    # EDID version 1.3
    # Digital Display
    **DisplaySize 480 270**
    Gamma 2.20
    Option "DPMS" "true"
    Horizsync 30-83
    VertRefresh 50-76
    # Maximum pixel clock is 170MHz
    #Not giving standard mode: 1920x1080, 60Hz
    #Not giving standard mode: 1280x720, 60Hz
    #Not giving standard mode: 1280x800, 60Hz
    #Not giving standard mode: 1280x1024, 60Hz
    #Not giving standard mode: 1600x900, 60Hz
    #Not giving standard mode: 1680x1050, 60Hz

    #Extension block found. Parsing...
    Modeline     "Mode 16" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 1" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 2" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 3" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
    Modeline     "Mode 4" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
    Modeline     "Mode 5" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
    Modeline     "Mode 6" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
    Modeline     "Mode 7" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 8" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
    Modeline     "Mode 9" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
    Modeline     "Mode 10" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
    Modeline     "Mode 11" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
    Modeline     "Mode 12" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
    Modeline     "Mode 13" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
    Modeline     "Mode 14" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
    Modeline     "Mode 15" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 17" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
    Modeline     "Mode 18" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync 
    Modeline     "Mode 19" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync 
    Option "PreferredMode" "Mode 16"
EndSection


```
The line I set bold gives the physical size of the display in mm; some programs make decisions regarding their graphical layout based on that data.

Holger

---

### Post by dam034 on 2019-11-16
So the result is this:

```
root@pcgame:~# get-edid|parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 5
No EDID on bus 6
No EDID on bus 7
No EDID on bus 8
No EDID on bus 9
No EDID on bus 11
2 potential busses found: 0 10
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
Bus 0 doesn't really have an EDID...
256-byte EDID successfully retrieved from i2c bus 10
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
	Identifier "LG TV"
	ModelName "LG TV"
	VendorName "GSM"
	# Monitor Manufactured week 1 of 2010
	# EDID version 1.3
	# Digital Display
	DisplaySize 160 90
	Gamma 2.20
	Option "DPMS" "false"
	Horizsync 30-83
	VertRefresh 58-62
	# Maximum pixel clock is 160MHz
	#Not giving standard mode: 1152x864, 75Hz
	#Not giving standard mode: 1280x1024, 60Hz

	#Extension block found. Parsing...
	Modeline 	"Mode 16" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
	Modeline 	"Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
	Modeline 	"Mode 1" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync 
	Modeline 	"Mode 2" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 3" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 4" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 5" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
	Modeline 	"Mode 6" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
	Modeline 	"Mode 7" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
	Modeline 	"Mode 8" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 9" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
	Modeline 	"Mode 10" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
	Modeline 	"Mode 11" 74.250 1920 2558 2602 2750 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 12" 74.250 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 13" 74.250 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
	Modeline 	"Mode 14" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
	Modeline 	"Mode 15" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
	Modeline 	"Mode 17" 74.25 1280 1344 1472 1664 720 723 728 732 +hsync +vsync 
	Modeline 	"Mode 18" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
	Modeline 	"Mode 19" 85.50 1360 1424 1536 1792 768 771 777 795 +hsync +vsync 
	Option "PreferredMode" "Mode 16"
EndSection
root@pcgame:~# 
```

I executed this command without changing any cable.

---

### Post by Holger_Gehrke on 2019-11-16
Well, that's really nice. Since parse-edid says the checksum matches the content of the edid data, the cable, the connectors and the memory inside the display storing the information are probably okay. 
But it looks like the display is lying like a champion. It says it's just 16 cm by 9 cm. This isn't all that unusual for older displays. You can inform X11 of the real size of the display by using the tool xrandr.
```

xrandr --output HDMI-0 --fbmm 960x540
```
The --output option takes the name of an output for a parameter. Run xrandr without any options to get the names of the outputs. The --fbmm option expects widthxheight in mm. The values I gave should be slightly to big for a 42" display.

Holger

---

### Post by hk42 on 2019-11-17
Hi
I too had this problem with VLC in 19.04 on a 1920x1080 TV.
It seems to have cured itself by magic :-)
The only thing I did was to install a lot of different windows managers:
XFCE ,Gnome and KDE .
But I have not yet tried different monitors.
Another thing I did was to switch from a 60 Hz refresh rate to a 50 Hz one
that seemed more suited to European TV's and videos.

---

### Post by dam034 on 2019-11-17
If I run xrandr, since I carry the PC from home to office, can I have problems with other monitors?

Thanks

---

### Post by Holger_Gehrke on 2019-11-18
'xrandr ... --fbmm' changes the display size X11 reports to programs for the specified output **for the current session only**. If you wanted to make that change permanent you'd have to either run xrandr with one of the ways to make programs autostart in the GUI or you could possibly write a xorg.conf fragment and drop it in /etc/xorg.conf.d (careful with that idea, doing something wrong in xorg.conf can break the GUI; it can be repaired but it's a bother). I haven't tried what happens if you connect to different displays over the course of one session, but of course you can run it multiple times in one session to adapt to different displays.

Holger

---

### Post by dam034 on 2019-11-20
I executed the command you wrote, but as you can see, nothing has changed.

```
root@pcgame:~# xrandr --output HDMI-A-0 --fbmm 960x540
root@pcgame:~# xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
DisplayPort-2 disconnected (normal left inverted right x axis y axis)
HDMI-A-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080     60.00*+  50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1680x1050     60.00  
   1280x1024     60.02  
   1440x900      60.00  
   1360x768      60.02  
   1280x800      60.00  
   1152x864      75.00  
   1280x720      60.96    60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
   720x400       70.08  
DVI-D-0 disconnected (normal left inverted right x axis y axis)
```

How can fix?

---

