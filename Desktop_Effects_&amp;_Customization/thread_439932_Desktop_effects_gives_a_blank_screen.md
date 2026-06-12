---
title: "Desktop effects gives a blank screen"
date: 2007-05-11
forum: Desktop Effects &amp; Customization
---

### Post by terabite on 2007-05-11
I have an 845G with 2.4GHz Intel with 256 MB DDR RAM.
When ever  i enable desktop effects, my screen goes blank (white)!!!!
What do i do? Please help!!!!:confused:

---

### Post by Pocadotty on 2007-05-11
I got that because of a lack of hardware acceleration. here is what I did to solve the problem

System-->Administration-->Restricted Drivers Manager

and I enabled my accelerated graphics driver.

Byrel then worked great.

Your system also might not be able to handle it. Byrel takes a fair amount of resources....

Also keep in mind that Byrel is beta software and may not work on certain hardware.  It also has some bugs on it.  If you cant get it to work with hardware acceleration (assuming you can do that) then your not likely to get it working.

Best of luck though, I hope everything works for you.


cheers :guitar:

---

### Post by terabite on 2007-05-11
:-(No.. I m not talkin about beryl.... Im talking about 'Desktop Effects' packaged by default in  Feisty Fawn
System > Preferences > Desktop Effects

It was working fine with my fedora core 6. So my system CAN support it.

---

### Post by dfreer on 2007-05-12
fedora core != ubuntu.

you DO need 3d acceleration (or direct rendering, same thing) enabled to use the Desktop Effects in ubuntu. You can find out whether you have direct rendering enabled with this command:
```
glxinfo | head
```
It will need to say Direct rendering = Yes, regardless of video card.
```
$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
**[B]direct rendering: Yes**[/B]
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float

```

fedora core 6 may have detected your video card correctly and automatically installed the correct video driver. Follow the instructions in the above post to see if Restricted Driver Manager can automatically detect and install the correct driver for you.

Also, Desktop Effects is basically a slimmed down version of compiz. Beryl is a fork of compiz. Therefore, when the above poster talks about beryl needing hardware acceleration (e.g. direct rendering, 3D Acceleration) he/she is correct. 

Desktop Effects / Beryl / Compiz are all beta software. As such, make sure you understand you may mess up your machine (although not to the point that you can't fix it).

---

### Post by terabite on 2007-05-13
Thanx dfreer.. I am a total newb to linux...
So excuse me if i say something stupid...

I already did what was mentioned in previous post but the when i clicked on restricted drivers manager, it said 'Your hardware doesnt require any restricted drivers'.
Also, device manager has  detected my video correctly (845G)
Also, I installed '**xserver-xorg-video-intel**', but din prove to b of any use....

This is what i got on giving the 'glxinfo | head' command:

```

$ glxinfo | head
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
name of display: :0.0


```
Can it be because i installed ubuntu in safe graphics mode?:confused: 

Sorry if i said anythn stupid.....:(

---

### Post by dfreer on 2007-05-13
nope, no stupid questions, don't worry about it :)
Actually, yeah it looks like something is borked up, go ahead and post the full ouput of glxinfo (because with | head it didn't quite catch the direct rendering line, I shoulda just had you grep for it but oh well). Also post your /etc/X11/xorg.conf file, you might need a different driver.

---

### Post by terabite on 2007-05-14
hehehe... thanx... 
But i tried running live CD again... on 'SAFE GRAPHICS' mode, it gives me same problem and works fine in normal graphics mode.
So its probably because i installed ubuntu on safe graphics mode so the generic driver was installed.
So ill reinstall my system and get back to you... 
Thanx for the help man! U really made me THINK!:KS 
:guitar:

---

### Post by terabite on 2007-05-14
Here is my xorg.conf file:

```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by terabite on 2007-05-14
heres the output of glxinfo. I don see any difference berween the head and this tho.....:confused: 
```

$glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

```

---

### Post by ruibuntu on 2007-05-14
What is your video card??

Ati or Nvidia?

---

### Post by esoterica on 2007-05-14
> **ruibuntu said:**
> What is your video card??

Ati or Nvidia?

His very first post says it's an 845G, which is niether nVidia or ATI, it's an Intel.

---

### Post by Dod_basim on 2007-05-14
sorry for interrupting.

same problem with **Intel Mobile 945GM/GMS/940GML**
same as *terabite* my glxinfo output is (i know it was 'okay' a couple a days ago)
```
name of display: :0.0
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  17
  Current serial number in output stream:  17

```
also when i start Beryl i get this blank white screen.

using Ubuntu Feisty on a thinkpad R60.

---

### Post by terabite on 2007-05-14
@ruibuntu:

No video card... as i said... Ive got onboard graphics...

---

### Post by dfreer on 2007-05-14
ok, go ahead and post your /etc/X11/xorg.conf file to back sure we are on the same page Dod_basim.

Yep, you are using the generic vesa driver terabite. you'll need to install the correct video driver, and then edit the Device Section of your /etc/X11/xorg.conf and change the driver from vesa to the driver for your graphics card (I believe it is i810). so here's what to do:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

```

find the Device section and change the driver from "vesa" to "i810":
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection
```
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection
```

Reboot. If X crashes all you have to do is hit <Ctrl><Alt><F5> and login. from there type this command to restore your xorg.conf backup:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Make sure to write that down because you won't be able to use internet like normal to view this post. If it does crash it is likely you do not have the driver installed correctly and we'll have to fix that. let us know!

EDIT: This may help:
[http://ubuntuforums.org/showthread.php?p=278456#post278456](http://ubuntuforums.org/showthread.php?p=278456#post278456)

---

### Post by rhonaldmoses on 2007-05-15
Refer the following link

[http://linuxevangelist.blogspot.com/2007/05/ubuntu-7-no-window-borders-on-desktop.html](http://linuxevangelist.blogspot.com/2007/05/ubuntu-7-no-window-borders-on-desktop.html)


and it's comments, I had tried something which worked for me (lazy to type them again, sorry).

Adios. :guitar:

---

### Post by terabite on 2007-05-15
Thanx guys... and a **SPECIAL THANX TO dfreer**!!!
My desktop effects are working now!!! I reinstalled it on 'normal' graphics mode!!!!
:guitar:

---

### Post by dfreer on 2007-05-15
For others that have this problem, what exactly did you do to fix? just change the driver from vesa to i810? Glad we helped!

---

### Post by Dod_basim on 2007-05-15
thanks!

---

