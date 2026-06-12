---
title: "[SOLVED] compiz problem in lenny"
date: 2008-04-20
forum: Debian
---

### Post by sujoy on 2008-04-20
i have debian lenny installed with the occasional package pulled in from Sid. its working fine, except for compiz

this is my /etc/apt/sources.list

> deb [http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/](http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/) ./
deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) lenny main contrib non-free
deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) sid main contrib non-free
deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) etch main contrib non-free
deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 DVD Binary-1 20080225-10:12]/ lenny contrib main

i installed the compiz-fusion-all package (just unmarked commpiz-kde since i use gnome), that shames repo is for emerald.

now when i do compiz --replace i get this error,

> 
sujoy@debian:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
sujoy@debian:~$ 


i am also including here my xorg.conf,

> Section "Files"
	Fontpath    "/usr/share/fonts/X11/misc"
	Fontpath    "/usr/share/fonts/X11/cyrillic"
	Fontpath    "/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath    "/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath    "/usr/share/fonts/X11/Type1"
	Fontpath    "/usr/share/fonts/X11/100dpi"
	Fontpath    "/usr/share/fonts/X11/75dpi"
EndSection


Section "Module"
	Load        "dbe"
	Load        "glx"
	Load        "dri"
	Load        "ddc"
	Load        "extmod"
	Load        "type1"
	Load        "freetype"
	Load        "bitmap"
	Load        "int10"
	Load        "vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82946GZ/GL Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option "AddARGBGLXVisuals" "True"
	Option "AllowGLXWithComposite" "True"
EndSection

Section "Monitor"
	Identifier	"S/T 57/56E/V"
	HorizSync       30.0-55.0
	VertRefresh     50.0-120.0
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82946GZ/GL Integrated Graphics Controller"
	Monitor		"S/T 57/56E/V"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1152x864"
		Virtual		1152 864
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Section "DRI"
	Mode 0666
EndSection

i am using the desktop mention in my sig, 
intel core 2 duo 1.86, intel D946GZIS motherboard with onboard intel graphics.

any help on this is highly appreciated.

---

### Post by prshah on 2008-04-20
> **sujoy said:**
> its working fine, except for compiz

now when i do compiz --replace i get this error,


What is the output of ```
glxinfo | grep -i direct
```? If it's yes, then i've shot my bolt. If it's No, then the out of  ```
LIBGL_DEBUG=verbose glxinfo
``` will give us a clue why direct rendering is disabled.

---

### Post by sujoy on 2008-04-20
> sujoy@debian:~$ glxinfo | grep -i direct
direct rendering: Yes


ah well, i will google for a bit long. last time around i got it working by following some guide, but for the life of me can't seem to find it anymore.

---

### Post by sujoy on 2008-04-20
problem solved :)

had to add this line 

> Option "XAANoOffscreenPixmaps" "true"

in xorg.conf under, Section "Device"

---

