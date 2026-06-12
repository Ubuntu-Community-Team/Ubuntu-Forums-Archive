---
title: "start X without monitor?"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by j_g on 2007-10-26
I have an X window app that I need to run after the computer boots. I added the app to gnome's "startup programs", so it starts up automatically. This app is controlled entirely via the keyboard. I also transport this computer to various places, and since the app is controlled via the keyboard (and starts up upon boot), I really don't need a monitor attached to operate the app. With feisty fawn, I used to be able to take the computer with me, power it up without a monitor attached, and Linux would boot up fine without any problems and the app would run.

I upgraded to the latest Ubuntu Studio (based on Gutsy Gibbon). If a monitor is not attached, the system will boot up into a dialog that says X can't be started, and asks if I want to reconfigure X. If not, it just dumps me into a command line, and of course, my X app doesn't start.

Two questions:

1) Is this a problem with only Ubuntu Studio? Will Gutsy Gibbon, like Feisty, successfully start up X even if a monitor is _not_ attached.

2) If this is a problem with Gutsy Gibbon's "bulletproofX", is there a way to disable bulletproofX so that the computer can boot X if no monitor is attached?

---

### Post by kidders on 2007-10-27
Hi there,

It's likely that what you're describing is by design, rather than a symptom of some sort of problem. For instance, this is my current xorg.conf...```
$ cat /etc/X11/xorg.conf
Section "ServerLayout"
        Screen 0		"Screen0" 0 0
        Identifier		"Default Layout"
        InputDevice		"Logitech Mouse"
        InputDevice		"Apple Keyboard" "CoreKeyboard"
EndSection

Section "Files"
        FontPath		"/usr/share/fonts/misc:unscaled"
        FontPath		"/usr/share/fonts/Type1"
        FontPath		"/usr/share/fonts/corefonts"
        FontPath		"/usr/share/fonts/freefonts"
        FontPath		"/usr/share/fonts/sharefonts"
        FontPath		"/usr/share/fonts/terminus"
        FontPath		"/usr/share/fonts/ttf-bitstream-vera"
        FontPath		"/usr/share/fonts/unifont"
        FontPath		"/usr/share/fonts/100dpi:unscaled"
        FontPath		"/usr/share/fonts/75dpi:unscaled"
        FontPath		"/usr/share/fonts/artwiz"
EndSection

Section "Module"
        Load		"xtrap"
EndSection

Section "InputDevice"
        Identifier	"Logitech Mouse"
        Driver		"evdev"
        Option		"Device" "/dev/input/event2"
        Option		"Protocol" "auto"
        Option		"CorePointer"
        Option		"Buttons" "17"
EndSection

Section "InputDevice"
        Identifier	"Apple Keyboard"
        Driver		"kbd"
        Option		"XkbRules" "xorg"
        Option		"XkbModel" "power_g5"
        Option		"XkbLayout" "us"
        Option		"XkbOptions" "lv3:lwin_switch"
        Option		"XkbVariant" "intl"
EndSection

Section "Monitor"
        Identifier	"Hanns G Monitor"
        VendorName	"Hanns G"
        ModelName	"HW191"
        Option		"DPMS"
EndSection

Section "Device"
        Identifier	"nVidia 8800"
        Driver		"nvidia"
        VendorName	"nVidia Corporation"
        BoardName	"8800"
        BusID		"PCI:2:0:0"
        Option		"NoLogo" "true"
        Option		"IgnoreDisplayDevices" "CRT, TV"
        Option		"AddARGBGLXVisuals" "true"
        Option		"UseEvents" "false"
        Option		"RenderAccel" "true"
        Option		"AllowDDCCI" "true"
        Option		"TripleBuffer" "true"
        Option		"BackingStore" "true"
        Option		"OnDemandVBlankInterrupts" "true"
EndSection

Section "Screen"
        Identifier	"Screen0"
        Device		"nVidia 8800"
        Monitor		"Hanns G Monitor"
        DefaultDepth	24
EndSection

Section "DRI"
        Group		0
        Mode		0666
EndSection

Section "Extensions"
        Option		"Composite" "enable"
EndSection
```I'm sure you'll agree that there's no way my X could start unless my monitor was connected and turned on at the time. If I wanted my X to be able to do that, I suppose I could've been more explicit about the configuration I wanted, but as things stand, I can't really expect X to autodetect my screen resolution, for instance, if the screen isn't there.

Anyhow, if you want your X to start without a screen (or maybe a mouse, etc.) attached, I suggest taking a look at your system logs & xorg.conf, and explicitly configuring anything that's currently being detected on the fly.

---

