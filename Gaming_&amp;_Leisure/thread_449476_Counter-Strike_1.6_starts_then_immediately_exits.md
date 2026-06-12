---
title: "Counter-Strike 1.6 starts then immediately exits"
date: 2007-05-20
forum: Gaming &amp; Leisure
---

### Post by rincewind1013 on 2007-05-20
I'm trying to get Counterstrike 1.6 to work in wine
I have not been successful
I followed the instructions at [http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554) and I have Steam working
It is display all of the windows correctly, fonts and everything

The problem is when I start Counterstrike
My resolution switches to 640x480 (since I havent gotten into the game to change the settings) and I see the menu screen graphic and then it goes away and I'm stuck at 640x480 until I change the resolution in Gnome

Here is the relevant info, let me know if you need anything more
Error Message:
```

$ wine Steam.exe 
fixme:process:IsWow64Process (0xffffffff 0x3d7e4c) stub!
fixme:shdocvw:ViewObject_SetAdvise (0xda21e10)->(1 00000002 0x1292e00)
fixme:shdocvw:PersistStreamInit_InitNew (0xda21e10)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xda21e10)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xda21e10)->(ffffffff)
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xda21ea4)->((null) 1 0x33bf0c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xda21ea4)->((null) 25 2 0x33bf20 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xda21ea4)->((null) 26 2 0x33bf20 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:shdocvw:ClientSite_GetContainer (0xda21ea4)->(0x33bf5c)
fixme:shdocvw:ClOleCommandTarget_Exec (0xda21ea4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33c080 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0xda61280)->(L"" L"" 0 0x33c094)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0xda61280)->(0x33c098 0x33bfbc)
fixme:shdocvw:ClOleCommandTarget_Exec (0xda21ea4)->((null) 29 2 0x33d708 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0xda21ea4)
err:systray:delete_icon invalid tray icon ID specified: 1
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x10b68d28)->(1 00000002 0x12935e0)
fixme:shdocvw:PersistStreamInit_InitNew (0x10b68d28)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10b68d28)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10b68d28)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x10b68d28)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x10b68d28)
fixme:shdocvw:OleObject_Close (0x10b68d28)->(1)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1a5020) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1a4038)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1a4038)->((nil),00000013)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1a4038)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:mshtml:hidden_proc (0x1009e 49225 0 1)
fixme:shdocvw:ViewObject_SetAdvise (0x1b5da8)->(1 00000002 0x7f6a48)
fixme:shdocvw:PersistStreamInit_InitNew (0x1b5da8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1b5da8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1b5da8)->(ffffffff)
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

```
At this point I am back in Gnome and I close Steam
```

err:ole:RevokeDragDrop invalid hwnd 0x1004c
err:ole:RevokeDragDrop invalid hwnd 0x10082
err:ole:RevokeDragDrop invalid hwnd 0x10084
err:ole:RevokeDragDrop invalid hwnd 0x10086
err:ole:RevokeDragDrop invalid hwnd 0x10088
err:ole:RevokeDragDrop invalid hwnd 0x1008a
err:ole:RevokeDragDrop invalid hwnd 0x1008c
err:ole:RevokeDragDrop invalid hwnd 0x20032
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xda21e10)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xda21e10)
fixme:shdocvw:OleObject_Close (0xda21e10)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0xda6d538)->((nil))
Unable to remove c:\program files\steam\shortcuts.dat!
Shutting down. . .

```

OS: Feisty Fawn with  2.6.20-15-generic
Wine: wine-0.9.37
Video Card: Intel X3000 (Integrated video on Intel DG965WH motherboard)
Video Driver: I've tried both intel and i810
Xorg.conf
```

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
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"Intel Corporation 82G965 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL 2005FPW"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82G965 Integrated Graphics Controller"
	Monitor		"DELL 2005FPW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
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

### Post by Erik Andrén on 2007-08-19
I do suffer from the same bug using the same graphics card. Please let me know if you have found an work-around for this bug.

---

### Post by mysticmatrix on 2007-08-25
Confirmed here too. I think we should start an online petition requesting Wine devolopers to support Intel IGP. I am even able to run far Cry decently under windows.

---

### Post by Mogurijin on 2007-08-25
Well, you could try a few things. One, you could have wine set up a virtual desktop so that if your games crash they don't mess up you resolution. Also the latest version of wine, .9.44 might work better for you guys ;)

---

### Post by mysticmatrix on 2007-09-02
> **Mogurijin said:**
> Well, you could try a few things. One, you could have wine set up a virtual desktop so that if your games crash they don't mess up you resolution. Also the latest version of wine, .9.44 might work better for you guys ;)

Doesn't works with virtual desktops and 0.9.44. See the link in my signature :(

---

