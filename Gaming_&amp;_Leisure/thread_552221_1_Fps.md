---
title: "1 Fps"
date: 2007-09-16
forum: Gaming &amp; Leisure
---

### Post by DeemiQ on 2007-09-16
Hello

I have a ATI x800 card and I have installed the driver for it but when I start a game the fps is around 1-2 FPS, I have tried second life and World of Warcraft. Anyone got an idea how to fix the problem?

Thanks in advance

---

### Post by buzzmandt on 2007-09-16
are you running it in wine or cedega
if wine you might run from terminal and it might show you error messages

---

### Post by tvrg on 2007-09-16
you say you installed the driver, but did you also configure X to use it?

post your xorg.conf please

---

### Post by DeemiQ on 2007-09-16
> **buzzmandt said:**
> are you running it in wine or cedega
if wine you might run from terminal and it might show you error messages
Wine.

This is what it says:
```

fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x194848) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x1944b0) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x194848) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x33f008,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wave:DSD_CreateSecondaryBuffer (0x202af8,0x33fcd0,180e8,0,0x203018,0x202f34,0x202ff8): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374026c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7d2fe4a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:d3d:state_psizemin WINED3DRS_POINTSIZE_MIN not supported on this opengl, value is 0.000000
err:d3d:state_multisampleaa Multisample antialiasing not supported by gl
fixme:d3d:state_psizemax WINED3DRS_POINTSIZE_MAX not supported on this opengl, value is 1.000000
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub
fixme:d3d:IWineD3DDeviceImpl_ResourceReleased Vertex buffer released while bound to a state block, stream 0
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

```

And this is my xorg.conf:

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
	Option		"XkbLayout"	"se"
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
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

### Post by misfitpierce on 2007-09-16
Could you possibly make sure drivers installed and working correctly by typing into terminal....

fglrxinfo

Post the output... If it says anything Mesa then you did not set it up right. It should only say ATI and so forth. If not on right Envy is a great tool for auto setting up newest ATI driver.

---

### Post by DeemiQ on 2007-09-16
> **misfitpierce said:**
> Could you possibly make sure drivers installed and working correctly by typing into terminal....

fglrxinfo

Post the output... If it says anything Mesa then you did not set it up right. It should only say ATI and so forth. If not on right Envy is a great tool for auto setting up newest ATI driver.
Hmm...

```

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

```

---

### Post by DeemiQ on 2007-09-16
Now it works!

I enabled the "ATI Accelerated graphics driver" in System -> Administration -> Restricted drivers

I disabled it before because it gives me bad video quality in VLC media player

---

### Post by DeemiQ on 2007-09-16
But now I have 20-30 fps instead >.<

EDIT:
Fixed some tweaks from a guide and now its much better (160 FPS when i'm standing still and around 30-60 fps when running around) I had max 60 fps on windows so I this is pretty good :))

---

