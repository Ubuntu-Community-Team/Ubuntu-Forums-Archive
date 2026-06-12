---
title: "glxinfo | grep rendering problem"
date: 2009-01-07
forum: Gaming &amp; Leisure
---

### Post by belowzero on 2009-01-07
A friend of mine is helping me to xfer to linux but the main thing I have to get running is WoW >.> however its very slow.
I read that when I do the 
```
glxinfo | grep rendering
```
im suppost to get a yes and im gettign this
```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

```
and I have a Sapphire ATI Radeon X1050

YES I dont expect no to lag with that card but GOD not even in a abandon area im save. there is always lag.

Any help will be appreciated

---

### Post by hikaricore on 2009-01-07
That mean you have to install your video drivers.
Right now it's like you're trying to run a toaster off of two D batteries.

Search around the forums for info on installing drivers for ATI cards.

Best of luck.

---

### Post by belowzero on 2009-01-07
I tough I was using them....
[http://s112.photobucket.com/albums/n168/kaboomco/?action=view&current=Screenshot-HardwareDrivers.png](http://s112.photobucket.com/albums/n168/kaboomco/?action=view&current=Screenshot-HardwareDrivers.png)
[IMG]http://s112.photobucket.com/albums/n168/kaboomco/?action=view&current=Screenshot-HardwareDrivers.png[/IMG]

```
 Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

```
 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X550/X700 Series
OpenGL version string: 1.4 (2.1.8087 Release)

```

I dont really know what to dO I have looked for things everywhere and it seems that my video card is not supported for this version of ubuntu which is 8.10
Again any help will be greatly appreciated

---

