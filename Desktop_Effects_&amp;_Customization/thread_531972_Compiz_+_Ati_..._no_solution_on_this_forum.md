---
title: "Compiz + Ati ... no solution on this forum?"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by bmdavis on 2007-08-22
After a few days of struggling, I've finally managed to install Feisty on my Dell Inspiron 6400.  With a X1400 Ati card, thanks a lot to posts in here (and mylittleubuntuguide.com).  Now comes the tricky part - making sure Compiz works.

Everything seems to be working fine in Feisty except this.  Others have encountered this problem. When we run the compiz --replace command, all get the same answer --
[B]
compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.[/B]

At this point you can find a hundred different posts on solutions, including fresh installs, uninstalls, editing sessions, etc.  Even editing xorg.conf (which will take you back to step 1, not permitting you to run linux on an ATI machine). 

So, where does that leave us?   Is this really--as it's been mentioned--a bug that hasn't been resolved for many users? Should we forget Compiz, realizing that while it pops up with Beryl we will never be able to use it? Do we mess with xorg or download envy?  Hate to oversimplify, but it seems that the posts just keep coming. Would love to hear some final solutions. 

huge thanks to all that contribute!!

---

### Post by Dark Star on 2007-08-22
Check thios thread for further queries [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

### Post by ricardoec on 2007-08-22
PlwAW, Ppost if this is a solution... I posted the same messae  three weeks ago and no one has it.

Cheers.

---

### Post by bmdavis on 2007-08-22
Again, this is the same thread (from Dark Star) that's been reposted over and over again.  When you run COMPIZ in terminal, the error still comes. EVEN AFTER FOLLOWING THE STEPS OVER AND OVER AGAIN.

Any other opinions?

---

### Post by levele304 on 2007-08-25
I have also been having the same problem, with no apparent solution. 

I have tried everything, literally every possible solution posted on this forum and nothing has worked.

I use an Ati X1400 vid card, and the error msg i get is :

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.


The 3D gears testing command in terminal shows the 3D gears turning (whch im guessing means my vid card is operational)

However Compiz fusion is still MIA.

---

### Post by levele304 on 2007-08-25
I just found this link posted on a different thread:

[http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=26907](http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=26907)

Well there it is, straight from the horses mouth

Apparently it really is impossible to get Compiz working with certain ATI cards for the time being.

Those of you who got it working apparently got lucky with manufacturer chips or something..

---

### Post by Rupertronco on 2007-08-25
It is possible to get fusion running on an x1400 but you need to use XGL. It's a complete pain and requires a ton of troubleshooting, but don't give up just yet. What driver are you using and what's your xorg.conf look like?

---

### Post by erfahren on 2007-08-25
I second what Rupertronco said. That ATI FAQ includes my card as well but I have compiz-fusion working with an XGL session.

Others have with the X1400 card. see this [Google search](http://www.google.com/search?hl=en&q=ubuntu+compiz+ati+x1400&btnG=Search).

---

### Post by levele304 on 2007-08-25
I am not sure what driver I am using as I used a customized install CD obtained from [www.mylittleubuntuguide.com](www.mylittleubuntuguide.com) which presumably came pre-customized for ATI vid cards.  How can I find this information? (terminal command of some sort?)

My xorg.conf file looks like this: (Sorry for the long code, I didnt know which specific area of code you were looking for since I know next to nothing of coding/programming)


Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	# Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

---

### Post by levele304 on 2007-08-25
oops double post

---

### Post by erfahren on 2007-08-25
> **levele304 said:**
> I am not sure what driver I am using as I used a customized install CD obtained from [www.mylittleubuntuguide.com](www.mylittleubuntuguide.com) which presumably came pre-customized for ATI vid cards.  How can I find this information? (terminal command of some sort?) ...

Interesting. Did you already try geting his newest update?

from your xorg.conf it appears that the ati propietary driver "fglrx" is loaded. ( type: fglrxinfo  into terminal to verify it's loaded and working. post the output of that.)

I'm not sure which version of the fglrx driver he's using in that CD, but I've tried the newer versions a couple of times (newer than what's in the Ubuntu repository) and had problems with them. I had to revert back. 

The display part of my xorg.conf looks like this (edit: included complete file): 
```

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"	"0"
        Option          "SHMConfig"             "true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

I'm sure others here would be able to help you more than I can. If you are using a newer version of the driver you might want to revert back and see if that helps. As I mentioned; I've done that but probably didn't do it the easiest way.  ( I disabled the new one in the "Restricted Drivers Manager" -- rebooted into regular session (not XGL) and removed xorg-driver-fglrx in Synaptic. downloaded the [Ubuntu one](http://packages.ubuntu.com/feisty/misc/xorg-driver-fglrx)  and installed it. I think I reinstalled linux-restricted-modules so the driver would be picked up in the Restricted Drivers Manager. )

Anyway, I posted back since no-one else has yet. hopefully someone will come along more knowledgeable than me!

---

### Post by Rupertronco on 2007-08-25
Go to a termain and type glxgears and see if it runs, that will check if your 3d acceleration is working. If it's not you've got to get the new fglrx driver. I'm pretty sure you need the newest for the x1*** cards. In your xorg.conf you have both AIGLX and compositing disabled, both are required for compiz-fusion to operate.

Edit: Open a terminal and type glxinfo and post the outcome of that command.

---

### Post by erfahren on 2007-08-26
> **Rupertronco said:**
> ... In your xorg.conf you have both AIGLX and compositing disabled, both are required for compiz-fusion to operate. ...

That's not true. fglrx doesn't support AIGLX (see [this thread](http://ubuntuforums.org/showthread.php?t=362525) ). That is why we have to run an XGL session for desktop effects. I edited my previous post to include my entire xorg.conf . I'm currently running Compiz-Fusion installed using a similar guide that the OP said he has tried. 

It seems like to me that his driver isn't configured correctly, or the xorg.cong file isn't listing his display properly at least. See how his Monitor, Video Card Device, and Screen sections are listed. (I really don't know a whole lot about this, but I know somethings wrong with that.) Any ideas of what's going on there?

It most likely has something to do with the [modified Ubuntu installation](http://www.mylittleubuntuguide.com/) he used and the way whatever version of the fglrx driver was installed/configured with it. That's why I suggested uninstalling the driver and installing the one from the Ubuntu repositories.

---

### Post by levele304 on 2007-08-26
glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6334 (8.34.8 ))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by levele304 on 2007-08-26
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8 )

---

### Post by Rupertronco on 2007-08-26
> **erfahren said:**
> That's not true. fglrx doesn't support AIGLX .

I thought the most recent drivers did support AIGLX? My apologies if I'm misinformed about the ATI products (nVidia here).

---

