---
title: "Nvidia Again"
date: 2005-04-09
forum: Desktop Environments
---

### Post by !nkubus on 2005-04-09
I jsuts installer a couple of hours ago Kubuntu :) i find relly cool and impresive.

but i followed ubuntuguide.org to install my nvidia drivers, and when i wan tto run my beloved games i get :
```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```


Here is the out put of my glxinfo:
```

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

```


here is my  glxgears:
```

Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual.

```
and finally here is my xorg.conf relevent parts:
```

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection


Section "Device"
	Identifier	"NVIDIA Corporation Geforce 440 MX"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation Geforce 440 MX"
	Monitor		"PHILIPS 107T"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
 ](*,)  ](*,) 
Any help would be appreciated :)

Thank you

---

### Post by whitehat on 2005-04-09
Ok, first off the Xorg.conf shows you running the default mesa driver ```
Driver   "nv"
```.  If you know you have the nvidia drivers installed you may want to change that to "nvidia" along with commenting out ```
Load   "glx"
``` and the entire dri section.  If you still have a problem, like x dies after restarting this, do an apt-get install lynx and lynx your way to nvidia.com and install the drivers by hand.  Should work otherwise.

---

### Post by digby on 2005-04-09
Are you certain about commenting out the "Load GLX" part?  I have perfectly functioning nVidia drivers, and that is still in there.

But about changing nv to nvidia, that is absolutely correct.

---

### Post by claudius on 2005-04-09
"load glx" should NOT  be commenting out. Only dri and glcore should be commented out :-)

---

### Post by dermotti on 2005-04-10
Claudius is right.

---

### Post by !nkubus on 2005-04-10
Thanks guys, this is was probably stupidiest error ever, i jsut tought that the  following command setted up the driver for me:

```

 sudo nvidia-glx-config enable

```

OK thank you for help

---

### Post by whitehat on 2005-04-23
[QUOTE=digby]Are you certain about commenting out the "Load GLX" part?  I have perfectly functioning nVidia drivers, and that is still in there.

But about changing nv to nvidia, that is absolutely correct.[/QUOTE]

woops, sorry, that's right do not comment "Load glx" out.

sorry about that

---

### Post by brannolte on 2005-10-25
same problem ... fast solution ... I like this forum

---

