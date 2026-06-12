---
title: "XIO:  fatal IO error 11 (Resource temporarily unavailable)"
date: 2009-01-06
forum: General Help
---

### Post by Vince4Amy on 2009-01-06
So I've just installed Ubuntu Hardy Heron 8.04 on this system with an ATI Radeon HD4850. I have installed all required updates and I've installed the proprietary graphics card drives. So the following is displayed:

fglrxinfo:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8304 Release
```


glxinfo | grep direct:

```
direct rendering: Yes
```

glxgears:

```
39624 frames in 5.0 seconds = 7924.776 FPS
40041 frames in 5.0 seconds = 8008.162 FPS
40040 frames in 5.0 seconds = 8007.918 FPS
39910 frames in 5.0 seconds = 7981.997 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 62 requests (61 known processed) with 0 events remaining.
```

So when I close glxgears I get that error which is shown above. It doesn't seem to affect 2d or 3d acceleration at all but I'd like to know whats causing that error at least.

---

### Post by SuperZ on 2009-04-26
yeaa.... me too... i get around the same thing exept my fps is way lower.

---

### Post by Frenziefrenz on 2009-06-09
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8664

$ glxinfo | grep direct
direct rendering: Yes
$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/175241 the monitor refresh rate.
14966 frames in 5.0 seconds = 2993.090 FPS
15277 frames in 5.0 seconds = 3055.336 FPS
15533 frames in 5.0 seconds = 3106.468 FPS
15447 frames in 5.0 seconds = 3089.275 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 39 requests (39 known processed) with 0 events remaining.

```

Same error... also a 4850. In 2D Ubuntu seems to run alright, with Compiz, however, it slows down to a crawl. Changing the size of a window, adding a new window (i.e. starting an application), each of those suddenly take like 5 seconds with Compiz enabled.

---

### Post by MattPhillips on 2009-07-18
Hello,

I have the same problem too--same error after glxgears and glxinfo.

Ubuntu 9.04. 64bit
HP elite e9180f
nVidia GTS 250

Here's my xorg.conf, which was modified from the original (presumably as a result of enabling the nVidia driver):

> Section "Monitor"
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
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

In terms of performance, everything seems to be working fine, even first-person shooters.  Direct rendering is enabled.  But I'd like to know what's going on, particularly as the fps I'm getting from glxgears seems lower than I would expect, about 7900.

If we could get some help here that would be greatly appreciated--this is clearly not an isolated problem.  Thank you!

Matt

---

### Post by MattPhillips on 2009-07-19
Okay, this is pretty strange--after a Ubuntu restart I ran glxgears again, and

1) Got much higher framerates, along the lines I would expect for the GTS 250--22000 instead of 7900

2) Something I had before but didn't mention: The first output from glxgears is the following:

> Running synchronized to the vertical refresh.  The framerate should be
approximately 1/602 the monitor refresh rate

However the fraction changes each time I do it; sometimes 1/2, 1/8, 1/302.  Obviously the value is ludicrous--my HP w2338h runs at 60Hz.  Wow, what's up with this?

3) Same error message as before.

Matt

---

### Post by the-penguin on 2010-02-03
ok 
I think that i have the same problem... i just cant see anything if i log my self in after installing the NVIDIA  driver but i created a root user

sudo passwd root

and when i log myself in using the username root and the password i just set then the display works..

wierd eh?
regards

da penguin

---

