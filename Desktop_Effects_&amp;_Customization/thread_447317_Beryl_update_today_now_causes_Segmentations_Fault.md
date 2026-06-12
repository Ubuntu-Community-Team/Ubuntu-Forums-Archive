---
title: "Beryl update today now causes Segmentations Fault"
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by orb9220 on 2007-05-17
After update today now beryl fails and falls back to metacity.

running beryl from term gives:

> orb@Two-Rivers:~$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

**Segmentation fault (core dumped)**

Any ideas why? using the trevino's svn 0.3

xorg

> Section "Monitor"
    Identifier     "A75f"
    Option         "DPMS"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"TwinView" "on"
        Option          "NvAGP" "3"
	Option		"MetaModes" "1280x1024,1280x1024; 1280x1024,NULL; 1024x768,1024x768; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "30-70"
	Option		"SecondMonitorVertRefresh" "60"
	Option		"TwinViewOrientation" "RightOf"		
	Option		"ConnectedMonitor" "CRT,CRT"
	Option 		"AllowGLXWithComposite" "true"
	Option		"RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"A75f"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"A75f"
	DefaultDepth	24
        Option	       "AddARGBVisuals"	   "True"
        Option         "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection


Using nvidia 9755
And Compiz is working fine.

---

### Post by russo.mic on 2007-05-18
Same here with ATI X1400 on a MacBook Pro.

Today's update causes Metacity.

Russo

---

### Post by Espreon on 2007-05-18
Me too. I am having a similar problem after todays updates even using Beryl's SVN like you.

---

### Post by DarkN00b on 2007-05-18
After I updated my Beryl this morning, it crashed and did not default to Metacity. Fortunately I had read that there was a problem with yesterday's update and had set Ubuntu to start in Metacity. So I open a terminal window and type "Beryl". Instantly I have borderless windows and an error about the benchmark plugin.

"AHA," I say to myself. 

So I type "Metacity" to restart my window manager. Then I start beryl-manager and go to Extras and disable the benchmark plugin. I restart Beryl and all is well in Ubuntuland. Beryl is running just fine now.

Oh yeah, I'm using Trevino's SVN as well.

---

### Post by Ender Black on 2007-05-18
DarkN00b... you.are.the.man!

Thanks.. that worked perfectly!

---

### Post by orb9220 on 2007-05-18
Yep just woke up and read my thread and you solved my plight!

Just disabled Benchmark and All is well.

DarkNoob I shall!

> Sacrifice! One Virgin Microsoft Employee to the Fires of Goddess Ubuntu in your Name!

---

### Post by Ivo Moelans on 2007-05-18
Yep, solved it for me too. Thanks.

---

### Post by Fireblend on 2007-05-18
Thanks, the same happened to me just now and I remembered reading this thread before so I checked it out and it worked. Thanks!

---

### Post by rfurman24 on 2007-06-26
Helped me too thanks

---

### Post by keesjelol on 2007-06-27
Alas, this does not work for me. I'm in the middle of trying to get compiz fusion to work and it looks like it would work if i went to compiz and the windows would have borders...

---

