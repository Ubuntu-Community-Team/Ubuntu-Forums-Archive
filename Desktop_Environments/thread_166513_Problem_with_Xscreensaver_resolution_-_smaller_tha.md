---
title: "Problem with Xscreensaver resolution - smaller than Xorg.conf resolution"
date: 2006-04-26
forum: Desktop Environments
---

### Post by mybootorg on 2006-04-26
**Pardon if I omit important info or get a Linux phrase here or there wrong. I am new to Ubuntu as of one week ago. Thanks.**

I'm running Ubuntu 5.10 on a Dell D610 Latitude Laptop docked and hooked up to a Dell 2001FPS running at 1600x1200 resolution.  My video card is an ATI Radeon Mobility M300 (M22) running on the "fglrx" driver.

The problem I am having is that when my screensaver starts, or I go to lock my workstation on my way to lunch, the lock screen or screensaver comes up at what looks like 1024x768 - in a smaller window - leaving the rest of my desktop exposed beneath it.

I feel like I have a pretty good grip on the two possible locations of the .xscreensaver files.  And also, I'm fairly certain I have xorg.conf set up properly (though I'm including it at the bottom of the post).  Likewise, I have no other problems with resolution except when the screensaver or lock screen comes on.  I can punch in my password and I'm back to 1600x1200 without any problems.

It "feels" to me like the screensaver is pulling its default resolution from somewhere other than what's currently running in Xserver, and somewhere other than the /etc/X11/xorg.conf file. But for the life of me, I can't figure out where or why this is occuring.

I have googled and searched these forums for someone else having the same problem but no dice there.

It should be noted that I originally install Ubuntu 5.10 without the Dell Flat Panel attached and using the default resolution of the laptop LCD panel which *is* 1024x768.  But I doubt an installation would hard code such a thing as a base resolution, and if so, I see no way to change it in the GUI.

Thanks in advance,

Craig Mitchell, St. Louis, Missouri

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
#  	SubSection "extmod"
#   	    Option "omit xfree86-dga"
#  	EndSubSection
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
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Dell 2001FPS"
	Option		"DPMS"
	HorizSync	31-81
	VertRefresh	60
	Modeline "1600x1200" 130.25 1600 1648 1680 1760 1200 1203 1207 1235
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Monitor		"Dell 2001FPS"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by mybootorg on 2006-05-02
I ****FINALLY**** found a solution to this.   The other day on a whim I installed the Gnome Screensavers package. Its pretty basic.  Not too many choices - like 3 or 4 choices of screensavers and none of them very interesting. But guess what. They run at the correct resolution and desklock works fine too.

This led me to investigate the problem from a strictly XScreensaver angle and the solution I found made me laugh.... it made me a laugh a big pirate laugh at the pure ridiculousness of it.  **[COLOR="Red"]HAR HARRRR HAR-HAR HARRRR HARRR![/COLOR]**

Here's what I found. From the Xscreensaver faq:

[QUOTE=Xscreensaver FAQ]This is a bug in the X server, not xscreensaver: the XF86VidModeGetViewPort() function is full of lies, and I don't see any way to work around it.

I believe this only happens on certain laptops, and possibly only on systems that have a docking station or external monitor that runs in a different resolution than the laptop's screen.[/quote]

Sound familiar?  Why yes it does...

[QUOTE=Xscreensaver FAQ]
There is discussion of this bug in the Red Hat and Debian bug systems; the buck was finally passed upstream to XFree86, where it is bug 421.

The XFree86 developers have closed the bug. As far as I can tell, their reason for this was, "this is an X server bug, but it's pretty hard to fix. Therefore, we are closing it."

So how about that. If you'd like them to actually fix this, you'll have to convince them that it matters, I guess...

In the meantime, you can work around this by editing your .xscreensaver file and setting the "GetViewPortIsFullOfLies" preference to True. That will make xscreensaver always run on the full size of the desktop, regardless of what lies the server tells about the currently-visible area. (This preference was added in version 4.16, May 2004.) [/QUOTE]

**[COLOR="Red"]HAR-HAR HARR![/COLOR]**

---

