---
title: "Warcraft 3"
date: 2006-10-29
forum: Gaming &amp; Leisure
---

### Post by MySweetTedy on 2006-10-29
Hello I am quite new to Ubuntu, I have a problem starting my Warcraft under it, first i tried to start with wine directly from my windows installation of warcraft, but it did not work and just threw me out to log in screen.

then i installed it new in my linux both ROC and TFT, everything was fine no mistakes during the installation, but when i try to start it with wine i throws me out to login screen again. i'm using wine "war3.exe" -opengl and just starting it from the directory where i've  installed it, does the same thing, i will be gr8ful at some help here

---

### Post by Mooie on 2006-10-29
it worked fine for me, both installing it with wine, and copying it over from my windows partition.  do you have the latest version of wine? you can get the latest version by uninstalling wine and adding this in synaptic or by putting it on the bottom of your /etc/apt/sources.list ```
deb http://wine.budgetdedicated.com/apt dapper main
```

I never used the -opengl option when i ran wc3, so try running the game without it, though enabling it will probably help.

also, you could try running 
wine "C:\Program Files\Warcraft III\war3.exe"
you dont have to cd to any directory for that either.  it emulates the path that it would be in windows.

hope it helps :D

---

### Post by MySweetTedy on 2006-10-29
Hmm, i reinstalled with new ver of Wine, but still the same problem, i wonder if it cannot come from that i have never installed any drivers on the ubuntu (6.10) for my video card (nvidia gforce 440 MX

---

### Post by Mooie on 2006-10-29
Yeah, you will need to get the drivers for your video card, the open source drivers (the default ones on the install) dont support 3d rendering very well.  If the card is newer then a geforce2 (i'm not familiar with your card) then just ```
apt-get install nvidia-glx
```  If the card is older than that and that driver isnt supported by the driver, then instead of nvidia-glx, use nvidia-letacy-glx (i think thats how its spelled)  once you have downloaded/installed the driver, you need to ```
gedit /etc/X11/xorg.conf
``` (you can replace gedit with any text editor if you want)
you need to go to the "Device" section of the file, and change ```
    Driver         "nv"
``` to say ```
    Driver         "nvidia"
```
then try running wc3, that should work :D

---

### Post by Mooie on 2006-10-29
after looking at the list of cards that require the legacy driver ([http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)), i'm pretty sure the nvidia-glx driver will work.

---

### Post by MySweetTedy on 2006-10-31
I have installed the proper driver for my Video card and my pc started working much better, also i have Dapper's 0.9.24 ver of wine (strangely it says it is for 6.06, and i am with 6.10) hmmm here is what i get:

```
root@Hardcore:/media/Work/games/Warcraft III# wine "Frozen Throne.exe"
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
err:wgl:X11DRV_wglGetProcAddress (wglGetIntegerv) - not found
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
fixme:advapi:SetSecurityInfo stub
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d8:IDirect3DDevice8Impl_CreateAdditionalSwapChain (0x18aed8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d8:IDirect3D8Impl_CreateDevice (0x18b060) D3D Initialization failed for WineD3DDevice 0x1af560
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create GLX context
fixme:d3d8:IDirect3DDevice8Impl_CreateAdditionalSwapChain (0x18aed8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d8:IDirect3D8Impl_CreateDevice (0x18b060) D3D Initialization failed for WineD3DDevice 0xe50020
fixme:imm:ImmAssociateContextEx ((nil), (nil), 16): stub
Xlib:  extension "GLX" missing on display ":0.0".

```

and i get a screen like in windows for starting Warcraft and also a alert msg that i dont have Direct X 8.1, and as far as i know Linux does not need Direct X...


Hmmm just tested it with -opengl and it almost starts but crashes after getting the mouse courser on a black screen and cannot even stop it anymore and must reboot

---

### Post by Mooie on 2006-10-31
hmmm, i'm not really sure whats wrong ](*,) 
it could be that your missing the an extension in your xorg.conf file, could you post the /etc/X11/xorg.conf please?

---

### Post by MySweetTedy on 2006-11-01
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SDM-HS73"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SDM-HS73"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Lord Illidan on 2006-11-01
Nice to see another Warcraft lover..

U have a mistake here :

```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
```

Change that to :

```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
```

---

### Post by MySweetTedy on 2006-11-01
illidan u the dota lord illidan??? I am trance)Adonis.. :P

So i corrected the file but still the same, warcraft starts  but i see my mouse on black screen, can it be something else i forgot to istall - fonts or something else on the grafics (the game would not start without the -opengl trigger)

and is there something like ctrl+alt+del to restart gnome?

illi if possible auth me for msn (the_wizard_wiz@hotmail.com) i have added you

---

### Post by Mooie on 2006-11-01
I have no idea what the problem is, it alwys just worked for me.
mabey you should run winecfg (just type winecfg in a console) and mess around with the options, make sure pixel shaders are enabled, and also make sure Direct3d vertex shader support is set to hardware, and make sure allow pixel shaders is checked.
you could also try setting the windows version (in the Applications tab) to windows 2000.   i hope some of this is helpful

---

### Post by dziubelis on 2006-11-02
Warcraft.
Well it took some time to launch it properly (I'm on Ubuntu 6.06).
I have nVidia 2 GeForce bassed card. So what I needed:
1. nVidia legacy drivers.
2. Plain Wine (no wine tools or anything, just Wine).
3. RoC and TFF cds + no/cd patches.

Installed nVidia drivers with 'Package Manager' (use search).

Installed Wine with 'Package Manager' according this:
[Link]("http://www.winehq.com/site/download-deb")

Ran 'winecfg' and set it to WinXP (Win2000 by default).

Ran 'sudo wine /media/cdom0/install.exe' (for both CDs)

Ran same commands to upgrade to 1.20e and apply no/cd patch.

All this was plain automatic, I did nothing more. All I did I have posted.

I did this twice and hade 2 different results:
1. To run warcraft I launch 'sudo wine [warcraft loader]', Warcraft runs slow (very very very very slow) (with and without -opengl), but I am able to connect to battle.net, start game etc.
2. To run Warcraft I must use war3.exe instead of no/cd loader, warcraft runs as fast as on WinXP (with and without -opengl), but I'm unable to connect to battle.net.

Second case wich I have now gives message:
Cant start war3.exe. Make sure the loader is in the same dir.

I must assure that loader IS in the same dir. I changed permissions of all files in Warcraft dir, but still same error message...

Wine ver. 0.9.24

Help :)

---

### Post by Mooie on 2006-11-06
i wouldnt use sudo to start or install the game (you dont need it, and you shouldnt use root access where it's not _really_ needed)

also, I would use windows 2000, not xp.  i'm not completely sure, but I think that some programs wont use newer librarys if its set to an older version.

you should not need the no/cd crack, those can cause you to not be able to use the game online.

I would reintsall the game (or copy the warcraft dir from a windows install into the correct directory in wine), then (with the frozen throne cd mounted) run ```
wine "C:\Program Files\Warcraft III\Frozen Throne.exe"  -opengl
```

it should run fine after that (i hope)

---

### Post by publicv on 2006-11-07
I also have a problem running warcraft 3 on ubuntu-

if I try wine War3.exe -opengl it doesn't seem to work at all:

```

fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x112e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1146,00007f03),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11ce,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbaef50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbaef88,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbac9bc,0x00000000), stub!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  464
  Current serial number in output stream:  464

```

if I try wine War3.exe I get the startup screen and the intro movie - but once i press a key to pass the intro movie it crushs with a message that is so long that this forum doesn't let me  post it (I will post it in 2 parts now)

---

### Post by publicv on 2006-11-07
```

fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 fun c=500 meth=0)
fixme:cursor:SetSystemCursor (0x112e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1146,00007f03),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11ce,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x7fd91190) : stub, emulati ng 64Mib for now, returning 64Mib
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(162,-1) not handled y et
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(163,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(164,1065353216) not h andled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(165,1) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(172,3) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(173,1) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(178,1065353216) not h andled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(179,1065353216) not h andled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(180,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(181,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(182,1065353216) not h andled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(183,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(184,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(190,15) not handled y et
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(191,15) not handled y et
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(192,15) not handled y et
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(193,-1) not handled y et
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(194,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(195,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(198,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(199,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(200,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(201,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(202,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(203,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(204,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(205,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(206,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(207,2) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(208,1) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd91190)->(209,1) not handled ye t
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
epoll_ctl: Operation not permitted
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f1 75-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f1 75-11d1-a392-00e0291f3959} not found
fixme:quartz:AVISplitter_InputPin_PreConnect process ODML header
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f1 75-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f1 75-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f1 75-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f1 75-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f1 75-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f1 75-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f1 75-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f1 75-11d1-a392-00e0291f3959} not found
fixme:mpeg3:MPEG3_StreamSize misses the block header overhead
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03 a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-002 0af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03 a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-002 0af0ba770}!
fixme:quartz:PullPin_Seek (0x7fd906b8)->(000000000, 7fffffffffffffff)
fixme:quartz:PullPin_BeginFlush (0x7fd906b8)->()
fixme:quartz:PullPin_EndFlush (0x7fd906b8)->()
Sorry, unknown layer type.
fixme:wave:DSD_CreateSecondaryBuffer (0x7fdb5f00,0x7c81e5ee,0,0,0x7cd606f4,0x7cd 60804,0x7cd606d0): stub
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Stream error
Stream error
Stream error
Stream error
Free format not supported.
Not supported!
Stream error
Not supported!
Not supported!
Sorry, unknown layer type.
mpg123: Can't rewind stream by 260 bits!
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Sorry, unknown layer type.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Sorry, unknown layer type.
Free format not supported.
Not supported!
Not supported!
Free format not supported.
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6216)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=5832)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=5352)
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Free format not supported.
Stream error
Free format not supported.
Sorry, unknown layer type.
Free format not supported.
Not supported!
Not supported!
Not supported!
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1576 < primar y_done=2248)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1576 < primar y_done=2248)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1576 < primar y_done=2248)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1576 < primar y_done=2248)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1576 < primar y_done=2248)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1576 < primar y_done=2248)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1576 < primar y_done=2248)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1128 < primar y_done=1800)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1416 < primar y_done=1480)
Not supported!
Stream error
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Not supported!
Free format not supported.
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Stream error
Free format not supported.
Free format not supported.
Free format not supported.
Stream error
Free format not supported.
Sorry, unknown layer type.
Free format not supported.
Not supported!
Not supported!
Not supported!
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2792)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2760)
Not supported!
Not supported!
Not supported!
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Stream error
Not supported!
Free format not supported.
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3560)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3560)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3560)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3560)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3560)
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Not supported!
Not supported!
Not supported!
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1576 < primar y_done=3400)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1160 < primar y_done=2984)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1224 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1384 < primar y_done=2152)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1416 < primar y_done=1640)
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Not supported!
Not supported!
Not supported!
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2184)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1416 < primar y_done=1864)
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2536)
Stream error
Not supported!
Free format not supported.
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1448 < primar y_done=1576)
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3040)
Sorry, unknown layer type.
Free format not supported.
Free format not supported.
big_values too large!
mpg123: Can't rewind stream by 15 bits!
Not supported!
Not supported!
Not supported!
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Not supported!
Not supported!
Not supported!
Sorry, unknown layer type.
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Free format not supported.
Free format not supported.
Free format not supported.
Not supported!
Not supported!
Not supported!
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Not supported!
Free format not supported.
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Stream error
Free format not supported.
Free format not supported.
Free format not supported.
Stream error
Free format not supported.
Sorry, unknown layer type.
Free format not supported.
Not supported!
Not supported!
Not supported!
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3560)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3560)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3560)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3560)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=3560)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1416 < primar y_done=3080)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1576 < primar y_done=2728)
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Not supported!
Not supported!
Not supported!
Sorry, unknown layer type.
Free format not supported.
Free format not supported.
Free format not supported.
Not supported!
Not supported!
Not supported!
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=5096)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=5096)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=5096)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=5096)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=5096)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=4936)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1384 < primar y_done=4552)

```

---

### Post by publicv on 2006-11-07
```

fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Not supported!
Free format not supported.
fixme:quartz:Filtergraph_QueryInterface unknown interface {56a868b2-0ad4-11ce-b0 3a-0020af0ba770}
[FAIL] s_pGraph->QueryInterface(IID_IMediaPosition, (void **)&pMP) = -2147467262 Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Free format not supported.
Stream error
Free format not supported.
Free format not supported.
Free format not supported.
Stream error
Free format not supported.
Sorry, unknown layer type.
Free format not supported.
Not supported!
Not supported!
Not supported!
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x7c45f250) : stub, emulati ng 64Mib for now, returning 64Mib
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6632)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6600)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6568)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6536)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6504)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6472)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6440)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6408)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6376)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6344)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=6312)
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(162,-1) not handled y et
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(163,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(164,1065353216) not h andled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(165,1) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(172,3) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(173,1) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(178,1065353216) not h andled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(179,1065353216) not h andled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(180,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(181,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(182,1065353216) not h andled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(183,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(184,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(190,15) not handled y et
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(191,15) not handled y et
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(192,15) not handled y et
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(193,-1) not handled y et
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(194,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(195,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(198,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(199,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(200,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(201,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(202,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(203,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(204,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(205,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(206,0) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(207,2) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(208,1) not handled ye t
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7c45f250)->(209,1) not handled ye t
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1576 < primar y_done=4104)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1576 < primar y_done=4104)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1544 < primar y_done=4072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1544 < primar y_done=4072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1544 < primar y_done=4072)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1512 < primar y_done=4040)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=2048 < primar y_done=2720)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7ef766c a

```

---

### Post by publicv on 2006-11-07
also - sound doesn't work properly in the intro video, and when i tried to config audio using winecfg it crushed when I clicked the audio tab saying:
```

Creating link /home/ido/.kde/socket-home.
can't create mcop directory

```

---

### Post by Mooie on 2006-11-07
in ubuntu sometimes the audio tab takes a few minutes to load, just wait a minute, then if it laods change the output to alsa.

also, what type of video card do you have? do you have the correct drivers that support hardware 3d rendering?

---

### Post by Mooie on 2006-11-07
i get the same error with winecfg, where it just kills the task, i'm not sure what to do :confused:  (though the gfx should work if you install the appropriate drivers for your card)

---

