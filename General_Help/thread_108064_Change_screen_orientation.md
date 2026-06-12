---
title: "Change screen orientation?"
date: 2005-12-24
forum: General Help
---

### Post by chimera on 2005-12-24
I was wondering, is there a way to change the screen orientation in Ubuntu? I've tried looking in NVIDIA settings, but there's no nvrotate like in windows. Any help would be appretiated.

---

### Post by stuporglue on 2005-12-25
You'll need to edit your xorg.conf manually, but it's possible. Make a backup first. :-) 

Try this link [http://wiki.x.org/X11R6.8.0/doc/fbdev.4.html](http://wiki.x.org/X11R6.8.0/doc/fbdev.4.html) , specificly the part that says 
> Option "Rotate" "string"
    Enable rotation of the display. The supported values are "CW" (clockwise, 90 degrees), "UD" (upside down, 180 degrees) and "CCW" (counter clockwise, 270 degrees). Implies use of the shadow framebuffer layer. Default: off. 


---

### Post by chimera on 2005-12-25
I'm confused, under which section am I supposted to put this option?

---

### Post by 23meg on 2005-12-25
You can also rotate on the fly with xrandr. Install it with ```
sudo apt-get install xrandr
``` if it's not installed and type ```
xrandr --help
``` for instructions. For Nvidia you have to add this line to the "Device" section of you xorg.conf file for it to work:```
       Option 	        "RandRRotation" "on"
```

---

### Post by chimera on 2005-12-25
chimera@chimera:~$ xrandr -o 1
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12


This is what xrandr spits out instead of rotating. And yes, I've added that option to xorg.conf. Am I doing something wrong?

---

### Post by 23meg on 2005-12-25
As far as I remember that's the error you should be getting when you haven't added the line. Are you 100% sure you've added it to the "Device" section? Also try the parameters "left", "right", "normal" and "inverted".

---

### Post by chimera on 2005-12-25
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RandRRotation" "on"
EndSection

those parameters give me the same error.

---

### Post by chimera on 2005-12-25
Anyone?

---

### Post by chimera on 2005-12-25
Nevermind, I got it working.

Turned out I just needed to restart X and GNOME after editing the xorg.conf file.

---

### Post by henriquemaia on 2006-04-22
[QUOTE=23meg]You can also rotate on the fly with xrandr. Install it with ```
sudo apt-get install xrandr
``` if it's not installed and type ```
xrandr --help
``` for instructions. For Nvidia you have to add this line to the "Device" section of you xorg.conf file for it to work:```
       Option 	        "RandRRotation" "on"
```[/QUOTE]

Thanks. Your advice did the trick.

---

