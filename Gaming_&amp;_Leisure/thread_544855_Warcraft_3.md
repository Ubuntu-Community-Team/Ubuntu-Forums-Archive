---
title: "Warcraft 3"
date: 2007-09-06
forum: Gaming &amp; Leisure
---

### Post by luxmeister on 2007-09-06
Hi, I'm a bit of a Linux newbie and im trying to get Warcraft 3 working with wine.
I installed ROC and frozen throne alright but when i ran the game using 
wine "Warcraft III.exe" -opengl   the game would launch but i was getting a horrible fps and this was just not the game but the menus were equally as slow.
i then updated the driver using  apt-get install nvidia-glx  and now i cannot run the game at all, i get this in the console:
```
 ~/.wine/drive_c/Program Files/Warcraft III$ wine war3.e
xe -opengl
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem
s
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 fun
c=500 meth=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem
s
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support
 !
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
\
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
err:d3d:InitAdapters Failed to initialize gl caps for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D8 is not available without opengl
```

this part is repeated about 1000 time...  "err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !"
i also get an error from warcraft 3 saying fatal error and it asks me to insert cd


it would be much appreciated if anyone could help me out
some other info:
distro: Kubuntu 7.04
wine version: 0.9.43
pc: amd 64 3200, nvidia 6600gt, 1g ram

---

### Post by BlahMan_of.Doom on 2007-09-06
What drivers do you have for your video card? nvidia-glx? or did you install using a third party program such as envy?

---

### Post by luxmeister on 2007-09-07
I installed a fresh copy of kubuntu 7.04 yesterday and was using those default drivers and i ran this command today to update them hoping it would improve the performance to a plable level (was getting less than 1fps)```
apt-get install nvidia-glx
``` 
after running that the drivers seemed to install without a hitch so yes i think i do have the nvidia-glx drivers
maybe this indicates problem  with opengl:
```
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support
 !
```

---

### Post by luxmeister on 2007-09-07
You can all stop panicking now...  i got it working
i changed my xorg.conf so that the driver was nvidia instead of nv
warcraft now runs as smoothly as it does on windows, i hope this helps other people who are new like me

---

### Post by Pikestaff on 2007-09-07
I have a similar problem and my driver is already set to nvidia... any ideas?

---

### Post by luxmeister on 2007-09-08
try these commands in the console to see if open gl is working:
```

glxinfo | grep -i opengl

```
```

glxinfo | grep direct

```
while i was having problems these commands returned errors (cant remember what) now that i have everything working it returns this:
```

------@------:~/$ glxinfo | grep -i opengl
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/PCI/SSE2
OpenGL version string: 2.1.0 NVIDIA 96.31
OpenGL extensions:
-------@-----:~/$ glxinfo | grep direct
direct rendering: Yes

```
if you think you have a similar problem to me then you might have a problem with either open gl or drivers,  try updating your drivers with 
```

apt-get install nvidia-glx

```
if that doesnt work you might need to install some packages to do with nvidia open gl, im not really sure about that bit. Im using kubuntu, with other distros it might be different (i have no idea)

---

### Post by Pikestaff on 2007-09-11
Thanks for the reply, OpenGL is working fine and other games run fine but not WC3.  I'll probably try updating the drivers though and seeing if that helps.

(I'm using Kubuntu also but Kubuntu Dapper, so it's an older version, so that might have to do with it too.)

---

