---
title: "Desktop Effects?"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by wuzuptravman on 2007-08-16
I want to turn on the desktop effects on my computer. It runs Ubuntu Feisty, and has no internet connection. It uses an Intel Pentium 3 processor. When I try to turn the effects on all I get is a blank white screen for a few seconds then it goes back. Is there any was to fix them?

---

### Post by sdowney717 on 2007-08-16
video card may not be supported, not powerful enough, etc....
One of my older PC has hercules card 64mb memory, but it will also do the white screen.

I run with an ATI 9600 and I have compiz-fusion and emerald themes working fine.

---

### Post by screaminj3sus on 2007-08-16
What is your video card?

---

### Post by wuzuptravman on 2007-08-20
i don't know how do i tell what my card is?

---

### Post by Parms on 2007-08-20
> **wuzuptravman said:**
> i don't know how do i tell what my card is?

If your still using windows you can go to control panel, device manager and click on the video card, and it should tell you what it is.

In Ubuntu goto 
System >> preferences >> Hardware Information

It will have a little chip picture.. Mine was by the way bottem, I'm also new to linux so I don't know how to tell which one it would be exactly. Because I already new what my card was. 

Best bet is to look at your computer specs online if, it was  astore bought computer with no additions. You can yahoo your computer and look up specs. 

Hope this helps at all. Sorry if it doesn't.

---

### Post by rainwalker on 2007-08-20
```
lspci|grep VGA
```

---

### Post by Rupertronco on 2007-08-20
You may need to get the computer an active internet connection in order to update the drivers. (I believe the restricted driver, which you'll probably need to use is not on the install cd).

---

### Post by wuzuptravman on 2007-08-21
i looked at the hardware info in my computer. I think this is my video card (it said something about graphic controller):

vendor: Intel Corporation

device: 82810E DC-133 CGC [Chipset

status: Status

bus type: PC

device type: Unknown

capabilities: Unknown

---

### Post by wuzuptravman on 2007-08-22
GLXinfo:

travis+AEA-travis-computer:+AH4AJA glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX+AF8-ARB+AF8-multisample, GLX+AF8-EXT+AF8-visual+AF8-info, GLX+AF8-EXT+AF8-visual+AF8-rating, 
    GLX+AF8-EXT+AF8-import+AF8-context, GLX+AF8-EXT+AF8-texture+AF8-from+AF8-pixmap, GLX+AF8-OML+AF8-swap+AF8-method, 
    GLX+AF8-SGI+AF8-make+AF8-current+AF8-read, GLX+AF8-SGIS+AF8-multisample, GLX+AF8-SGIX+AF8-hyperpipe, 
    GLX+AF8-SGIX+AF8-swap+AF8-barrier, GLX+AF8-SGIX+AF8-fbconfig, GLX+AF8-MESA+AF8-copy+AF8-sub+AF8-buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX+AF8-ARB+AF8-get+AF8-proc+AF8-address, GLX+AF8-ARB+AF8-multisample, GLX+AF8-EXT+AF8-import+AF8-context, 
    GLX+AF8-EXT+AF8-visual+AF8-info, GLX+AF8-EXT+AF8-visual+AF8-rating, GLX+AF8-MESA+AF8-allocate+AF8-memory, 
    GLX+AF8-MESA+AF8-copy+AF8-sub+AF8-buffer, GLX+AF8-MESA+AF8-swap+AF8-control, 
    GLX+AF8-MESA+AF8-swap+AF8-frame+AF8-usage, GLX+AF8-OML+AF8-swap+AF8-method, GLX+AF8-OML+AF8-sync+AF8-control, 
    GLX+AF8-SGI+AF8-make+AF8-current+AF8-read, GLX+AF8-SGI+AF8-swap+AF8-control, GLX+AF8-SGI+AF8-video+AF8-sync, 
    GLX+AF8-SGIS+AF8-multisample, GLX+AF8-SGIX+AF8-fbconfig, GLX+AF8-SGIX+AF8-pbuffer, 
    GLX+AF8-SGIX+AF8-visual+AF8-select+AF8-group, GLX+AF8-EXT+AF8-texture+AF8-from+AF8-pixmap
GLX version: 1.2
GLX extensions:
    GLX+AF8-ARB+AF8-get+AF8-proc+AF8-address, GLX+AF8-ARB+AF8-multisample, GLX+AF8-EXT+AF8-import+AF8-context, 
    GLX+AF8-EXT+AF8-visual+AF8-info, GLX+AF8-EXT+AF8-visual+AF8-rating, GLX+AF8-MESA+AF8-copy+AF8-sub+AF8-buffer, 
    GLX+AF8-OML+AF8-swap+AF8-method, GLX+AF8-SGI+AF8-make+AF8-current+AF8-read, GLX+AF8-SGIS+AF8-multisample, 
    GLX+AF8-SGIX+AF8-fbconfig, GLX+AF8-EXT+AF8-texture+AF8-from+AF8-pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL+AF8-ARB+AF8-depth+AF8-texture, GL+AF8-ARB+AF8-draw+AF8-buffers, GL+AF8-ARB+AF8-fragment+AF8-program, 
    GL+AF8-ARB+AF8-imaging, GL+AF8-ARB+AF8-multisample, GL+AF8-ARB+AF8-multitexture, 
    GL+AF8-ARB+AF8-occlusion+AF8-query, GL+AF8-ARB+AF8-point+AF8-parameters, GL+AF8-ARB+AF8-point+AF8-sprite, 
    GL+AF8-ARB+AF8-shadow, GL+AF8-ARB+AF8-shadow+AF8-ambient, GL+AF8-ARB+AF8-texture+AF8-border+AF8-clamp, 
    GL+AF8-ARB+AF8-texture+AF8-compression, GL+AF8-ARB+AF8-texture+AF8-cube+AF8-map, 
    GL+AF8-ARB+AF8-texture+AF8-env+AF8-add, GL+AF8-ARB+AF8-texture+AF8-env+AF8-combine, 
    GL+AF8-ARB+AF8-texture+AF8-env+AF8-crossbar, GL+AF8-ARB+AF8-texture+AF8-env+AF8-dot3, 
    GL+AF8-ARB+AF8-texture+AF8-mirrored+AF8-repeat, GL+AF8-ARB+AF8-texture+AF8-non+AF8-power+AF8-of+AF8-two, 
    GL+AF8-ARB+AF8-texture+AF8-rectangle, GL+AF8-ARB+AF8-transpose+AF8-matrix, GL+AF8-ARB+AF8-vertex+AF8-program, 
    GL+AF8-ARB+AF8-window+AF8-pos, GL+AF8-EXT+AF8-abgr, GL+AF8-EXT+AF8-bgra, GL+AF8-EXT+AF8-blend+AF8-color, 
    GL+AF8-EXT+AF8-blend+AF8-equation+AF8-separate, GL+AF8-EXT+AF8-blend+AF8-func+AF8-separate, 
    GL+AF8-EXT+AF8-blend+AF8-logic+AF8-op, GL+AF8-EXT+AF8-blend+AF8-minmax, GL+AF8-EXT+AF8-blend+AF8-subtract, 
    GL+AF8-EXT+AF8-clip+AF8-volume+AF8-hint, GL+AF8-EXT+AF8-copy+AF8-texture, GL+AF8-EXT+AF8-draw+AF8-range+AF8-elements, 
    GL+AF8-EXT+AF8-fog+AF8-coord, GL+AF8-EXT+AF8-framebuffer+AF8-object, GL+AF8-EXT+AF8-multi+AF8-draw+AF8-arrays, 
    GL+AF8-EXT+AF8-packed+AF8-pixels, GL+AF8-EXT+AF8-paletted+AF8-texture, GL+AF8-EXT+AF8-point+AF8-parameters, 
    GL+AF8-EXT+AF8-polygon+AF8-offset, GL+AF8-EXT+AF8-rescale+AF8-normal, GL+AF8-EXT+AF8-secondary+AF8-color, 
    GL+AF8-EXT+AF8-separate+AF8-specular+AF8-color, GL+AF8-EXT+AF8-shadow+AF8-funcs, 
    GL+AF8-EXT+AF8-shared+AF8-texture+AF8-palette, GL+AF8-EXT+AF8-stencil+AF8-wrap, GL+AF8-EXT+AF8-subtexture, 
    GL+AF8-EXT+AF8-texture, GL+AF8-EXT+AF8-texture3D, GL+AF8-EXT+AF8-texture+AF8-edge+AF8-clamp, 
    GL+AF8-EXT+AF8-texture+AF8-env+AF8-add, GL+AF8-EXT+AF8-texture+AF8-env+AF8-combine, 
    GL+AF8-EXT+AF8-texture+AF8-env+AF8-dot3, GL+AF8-EXT+AF8-texture+AF8-lod+AF8-bias, 
    GL+AF8-EXT+AF8-texture+AF8-mirror+AF8-clamp, GL+AF8-EXT+AF8-texture+AF8-object, 
    GL+AF8-EXT+AF8-texture+AF8-rectangle, GL+AF8-EXT+AF8-vertex+AF8-array, GL+AF8-APPLE+AF8-packed+AF8-pixels, 
    GL+AF8-ATI+AF8-draw+AF8-buffers, GL+AF8-ATI+AF8-texture+AF8-env+AF8-combine3, 
    GL+AF8-ATI+AF8-texture+AF8-mirror+AF8-once, GL+AF8-ATIX+AF8-texture+AF8-env+AF8-combine3, 
    GL+AF8-IBM+AF8-texture+AF8-mirrored+AF8-repeat, GL+AF8-INGR+AF8-blend+AF8-func+AF8-separate, 
    GL+AF8-MESA+AF8-pack+AF8-invert, GL+AF8-MESA+AF8-ycbcr+AF8-texture, GL+AF8-NV+AF8-blend+AF8-square, 
    GL+AF8-NV+AF8-fragment+AF8-program, GL+AF8-NV+AF8-light+AF8-max+AF8-exponent, GL+AF8-NV+AF8-point+AF8-sprite, 
    GL+AF8-NV+AF8-texgen+AF8-reflection, GL+AF8-NV+AF8-texture+AF8-rectangle, GL+AF8-NV+AF8-vertex+AF8-program, 
    GL+AF8-NV+AF8-vertex+AF8-program1+AF8-1, GL+AF8-SGI+AF8-color+AF8-matrix, GL+AF8-SGI+AF8-color+AF8-table, 
    GL+AF8-SGIS+AF8-generate+AF8-mipmap, GL+AF8-SGIS+AF8-texture+AF8-border+AF8-clamp, 
    GL+AF8-SGIS+AF8-texture+AF8-edge+AF8-clamp, GL+AF8-SGIS+AF8-texture+AF8-lod, GL+AF8-SGIX+AF8-depth+AF8-texture, 
    GL+AF8-SGIX+AF8-shadow, GL+AF8-SGIX+AF8-shadow+AF8-ambient, GL+AF8-SUN+AF8-multi+AF8-draw+AF8-arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x43 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
travis+AEA-travis-computer:+AH4AJA 

xorg.conf:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
EndSection

Section "Monitor"
	Identifier	"DELL M780"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Monitor		"DELL M780"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
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

---

### Post by Aquilastudio.com on 2007-08-22
Many people have the same problem.
You are not special:(
In order to fix the problem get [COLOR="Red"]XGL[/COLOR]
Go to the Terminal, type in 
```
sudo apt-get install xserver-xgl
```
Now [COLOR="Red"]XGL[/COLOR] is installed you have to set it up
In the Terminal type in
```
sudo gedit /usr/local/bin/startxgl.sh
```
In the text box type in:
For Gnome and Nvida graphics card type in:
```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session

```
For KDE change the last line to 
```
exec startkde
```
For ATI Graphics Cards:
```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session
```
Save It and in the terminal type in
```
$ sudo chmod a+x /usr/local/bin/startxgl.sh
```
Now we create the login session.
```
$ sudo gedit /usr/share/xsessions/xgl.desktop
```
In the text window type in:
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```
Save it and you are done!
Logout and in the sessions choose XGL and GNOME.
Now your effects should work

---

