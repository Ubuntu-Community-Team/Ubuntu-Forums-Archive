---
title: "OpenGL / GLX stopped working"
date: 2008-02-15
forum: Desktop Environments
---

### Post by ad_267 on 2008-02-15
Hi

Until recently I could play OpenGL games fine but now I can't. I'm not sure what I changed because I don't play games very often.

When I try to run VegaStrike for example I get the error message:
```
freeglut (./vegastrike): OpenGL GLX extension not supported by display ':0.0'
```

And when I run glxgears I get this message:
```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```

I'm running Ubuntu 7.10 Gutsy Gibbon and I have an nVidia Geforce 6600gt. I'm using the nvidia drivers and I've attached my xorg.conf file.

I tried reinstalling nvidia-glx-new and running nvidia-glx-config enable which I saw suggested on this forum for someone else having the same problem but this didn't work.

Thanks for your suggestions,
Adam

---

### Post by georgezzz on 2008-02-15
what happened when you ran the nvidia-glx-config enable?

---

### Post by ad_267 on 2008-02-15
When I ran that I think I had a message about my xorg.conf having been changed so I updated the md5 hash and then ran it again. I then restarted and when I loaded back up I had only one screen working (I have two) and it was at 1024x768 instead of 1280x1024. I ran glxgears which still didn't work then then I opened up the nvidia-settings tool to increase the resolution and enable the other monitor.

Also something that may or may not be related is that I don't think I could ever enable desktop effects, I always got a message saying they couldn't be enabled.

Edit: Am I supposed to be using the nvidia-glx-new driver or should I try the nvidia-glx one?

---

### Post by ad_267 on 2008-02-15
I tried adding Load "glx" under Section "Module" in my xorg.conf file but that didn't help. I also tried running nvidia-xconfig but that didn't help either.

This is my output from glxinfo but I don't think it will be very helpful:
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0xd3 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

---

### Post by ad_267 on 2008-02-16
In my /var/log/Xorg.0.log file I found these lines:

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000042gl
(EE) Failed to load /usr/lib/xorg/modules//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)

And then these lines further down:

(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

How do I know if the module is the NVIDIA GLX module?
Using locate libglx.so I found these:
/usr/lib/xorg/modules/extensions/libglx.so.169.09
/usr/lib/xorg/modules/extensions/libglx.so
/usr/lib/xorg/modules/libglx.so
/usr/lib/xorg/modules/libglx.so.100.14.19

---

### Post by ad_267 on 2008-02-17
Doesn't sound like anyone could help so I've just reinstalled ubuntu and now everything works fine. I think the problem may be that I once tried installing the drivers from the nvidia website but then reverted back because they weren't working properly.

My desktop effects are also working with one monitor but I think adding the second monitor might have been what stopped them working last time.

---

### Post by Jens Albretsen on 2008-02-17
Had same problem, I just executed the following in a shell.
"sudo ln -sf /usr/lib/xorg/modules/extensions/libglx.so.169.09 /usr/lib/xorg/modules/libglx.so"
now it works for me again.

---

### Post by ad_267 on 2008-02-17
I tried that but I got a message about the nvidia driver version being different from the kernel or something. Oh well it's all working now. I even got the desktop effects working, just had to use TwinView instead of xinerama

---

