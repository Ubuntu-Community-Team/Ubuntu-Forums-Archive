---
title: "Multimedia Keys remapping"
date: 2009-06-04
forum: Desktop Environments
---

### Post by Blastz on 2009-06-04
Hi, 

I'm remapping some of my multimedia keys so they work with XBMC. I'm using XEV to find out the keycodes and modifying ~/.Xmodmap. I'm having two issues:

1. I want the FastForward button to be a keypress event, not keymapnotify, so I can bind it to a normal key, ie F. 

For example, XEV reports Vol- as being a Keypress event but Vol+ and mute as being a keymapnotify with FocusIn FocusOut events. I've found that using the keyboard settings in the Xfce settings manager I have bound this correctly and Vol- now correctly reports as a keymapnotify. FastForward is not listed in the keyboard settings.

2. I am setting up a Logitech UltraX Media Remote. This [wiki]("http://www.mythtv.org/wiki/Logitech_UltraX_Media_Remote"),  states that I modify Xorg.conf, however anything I do to Xorg.conf messes up the display. So for now I've left it alone but cannot use all the keys.


my Xorg looks like this:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection



Thanks

---

