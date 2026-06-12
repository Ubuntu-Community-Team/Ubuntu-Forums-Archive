---
title: "Window Panning - Resolution higher than supported"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by ziaziu on 2007-09-28
Hello, 

I have a Compaq Presario M200z laptop which natively supports a resolution of 1024x768.  I read around the net snippets where people were able to somehow enable a higher resolution on their screens (don't know if CRT's or LCD's), but the desktop was ACTUALLY their natively supported resolution just stretched beyond the physical screen borders.  The screen then 'shifted' around with the pointer.
To illustrate:
I have a resolution of 1024x768 but would like, say, 1600x1200 resolution. I know that the screen won't handle it, so...I would like my desktop to change to a 'virtual' one where it is much larger than my screen and I can scroll around it with my mouse (or a scrollbar?).

I have a ATI Radeon XPress 200M graphics card.

Thanks!

---

### Post by ziaziu on 2007-10-01
I got it to work! Partially at least. 

The trick is to edit the xorg.conf file.  Of course, first back up the working xorg.conf file (located in /etc/X11/).  The resolution that my monitor supporst natively is 1024x768.  but for some applications I needed a higher resolution.  So this is how I did it:

I have an ATI Radeon XPRESS 200M card configured with the proprietary drivers.  I don't think this is completely necessary, but just wanted it.  As long as the xorg.conf file is correctly configured and your X windows environment is working to start with, this should be a piece of cake.

```
 cd /etc/X11/
```
```
cp xorg.conf xorg.conf.bkup
```
```
sudo gedit xorg.conf
```

on KDE (kubuntu) use 'kate' instead of 'gedit' and on xubuntu use 'mousepad' instead of 'gedit.

Go to the  section "Screen" >> SubSection "Display"  and add this line:
Virtual		1280 1024

This Section and Subsection can be present TWICE!!  this occurred after I installed my ATI drivers successfully.  Hence, add the above line to BOTH sections.  Here is a section of my xorg.conf file :  (the "Modes" line isn't that important :/)

...
...
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
...
...
...
	SubSection "Display"
		Depth	24
		Modes		"1024x768"
		Virtual		1280 1024
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
		Modes		"1600x1400"	"1280x1024"	"1024x768"	"800x600"
		Virtual		1280 1024
	EndSubSection
EndSection

Now you can use xrandr to change the resolution on the fly by typing the command:
```
xrandr -q 
```      To print out the available modes/sizes.  This requires you to install 'xrandr'.  To do this just type:
```
sudo apt-get update
sudo apt-get install xrandr
```

Once you know what you want type:
```
xrandr -s [SIZE/OPTION]  
``` 

[SIZE="3"]Example: [/SIZE] 

The printout of my xrandr -q command is:
```
sl@sl-laptop:~$ xrandr -q
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 301mm x 230mm )  *60  
 1    800 x 600    ( 301mm x 230mm )   60  
 2    848 x 480    ( 301mm x 230mm )   60  
 3    720 x 576    ( 301mm x 230mm )   60  
 4    720 x 480    ( 301mm x 230mm )   60  
 5    640 x 480    ( 301mm x 230mm )   60  
 6    640 x 400    ( 301mm x 230mm )   60  
 7    640 x 350    ( 301mm x 230mm )   60  
 8    512 x 384    ( 301mm x 230mm )   60  
 9    400 x 300    ( 301mm x 230mm )   60  
 10   320 x 240    ( 301mm x 230mm )   60  
 11   320 x 200    ( 301mm x 230mm )   60  
 12  1280 x 1024   ( 301mm x 230mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none

```

and to use the option nr 12 type:    ```
xrandr -s 12
```

Now the only problem is that my GDM screen is automatically in the virtual resolution, so it is a bit inconvenient to have to log in and type the xrandr command each time I reboot.  I will look into when I have more time.

---

