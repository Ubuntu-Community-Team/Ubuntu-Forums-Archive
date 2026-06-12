---
title: "Desktop effects could not be enabled after installing 7600GS"
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by ashkev on 2007-12-21
I had Compiz-fusion running after some tweaking using my onboard intel graphics accelerator.  I just installed a GeForce 7600 GS and now, I can't enable desktop effects.  I am not sure if I have the right driver installed? In xorg.conf I have:
```
Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection
```

I als tried:
```
kevin@edubuntu:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

So something aint right....

---

### Post by Nano Geek on 2007-12-21
Go to **Add/Remove...** and search for **NVidia binary X.Org driver**. Install that package, reboot, and Desktop Effects should be working.

---

### Post by ashkev on 2007-12-21
I had tried installing the driver, but I got errors about linux-headers.  I logged in with a different kernal and was able to install it no problem.

---

### Post by Nano Geek on 2007-12-21
That's funny, was it a custom kernel?

---

### Post by ashkev on 2007-12-23
Now, I seem to recall installing some sort of experimental kernel with the intention of removing it right away, and I guess I didn't.  It was 2.6.23-rc2-686.  I can boot using  2.6.22-14-generic but how do I go back to the standard kernel?

---

### Post by Nano Geek on 2007-12-24
Ahh.

I see.

Merry Christmas.

---

### Post by Sef on 2007-12-25
> Now, I seem to recall installing some sort of experimental kernel with the intention of removing it right away, and I guess I didn't. It was 2.6.23-rc2-686. I can boot using 2.6.22-14-generic but how do I go back to the standard kernel?

How did you install that kernel?

---

### Post by Zorael on 2007-12-25
I think you can get back to the default kernel by calling
```
$ sudo dpkg-reconfigure linux-image-2.6.22-14-generic
```
Replace generic with other flavours if you're not running an x86 machine. Perhaps just configuring the "linux-image-generic" package works?

As for desktop effects, you don't seem to be using the proprietary accelerated nvidia driver. You could remedy this through the Restricted Modules app, I believe, or by manually editing /etc/X11/xorg.conf.

You'll want to have it say
```
Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"**nvidia**"
	BusID		"PCI:1:0:0"
EndSection
```
...instead.

---

