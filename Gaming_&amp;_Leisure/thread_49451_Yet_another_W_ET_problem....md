---
title: "Yet another W: ET problem..."
date: 2005-07-16
forum: Gaming &amp; Leisure
---

### Post by traherom on 2005-07-16
Using a version of ET scp'd off the Ohio Supercomputer Center's BALE cluster (yes, I actually have an account there), I try to run Enemy Territory, but get:
> Xlib:  extension "XFree86-VidModeExtension" missing on display "192.168.2.39:0.0".
Received signal 11, exiting...

Hm... how can I enable/get the "VidModeExtension?" Thanks in advance.

--EDIT--
I just tried it with the installer. Same error.

---

### Post by endy on 2005-07-16
Do you have the following line as part of the modules section of your xorg.conf file?

```
Load	"extmod"
``` 

I believe thats where it gets loaded, you can check with the following command:

```
xdpyinfo | grep VidModeExtension
```

---

### Post by traherom on 2005-07-16
[QUOTE=endy]Do you have the following line as part of the modules section of your xorg.conf file?

```
Load	"extmod"
```[/quote]Already there. :( (Assuming you mean the xorg in /etc/X11)

[quote=endy]I believe thats where it gets loaded, you can check with the following command:

```
xdpyinfo | grep VidModeExtension
```[/QUOTE]
Nope... no output.

Thanks for the reply.

---

### Post by traherom on 2005-07-18
SO... I got past my earlier error, but now I get:
> GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...


---

### Post by endy on 2005-07-18
What graphics card and drivers are you using? If it's an nvidia card you need to install the nvidia drivers via apt-get or synaptic. 

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

