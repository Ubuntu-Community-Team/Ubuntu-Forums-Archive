---
title: "i810 really slow... and WC3 doesn't work"
date: 2006-09-12
forum: Desktop Environments
---

### Post by blacktorch on 2006-09-12
Hello, I have a few problems with my laptop. It uses an Intel 915 chipset, i810 driver... 

glxgears doesn't return any fps count or anything. Simple games such as Neverball are running unusually slow.

-------------
When I do 'wine war3.exe -opengl' I get this (and nothing else happens):
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:d3d:IWineD3DImpl_FillGLCaps >>>>>>>>>>>>>>>>> 501 from extension detection @ directx.c / 753
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f67c,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  400
  Current serial number in output stream:  400

-------------
glxinfo | grep rendering
direct rendering: Yes

-------------
dmesg | grep -i agpgart
[17179587.232000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.236000] agpgart: Detected an Intel 915GM Chipset.
[17179587.240000] agpgart: Detected 7932K stolen memory.
[17179587.260000] agpgart: AGP aperture is 256M @ 0xc0000000

---

### Post by NMUrugbysteve on 2006-09-12
Are you running wine.09.20? because i've been having those problems too, i just reverted back to 0.9.19. and with glxgears be sure to pass the "-printfps" option.

---

### Post by blacktorch on 2006-09-12
OK thanks, will try wine 0.9.19 soon then. 

glxgears -printfps
3864 frames in 5.0 seconds = 772.616 FPS
4113 frames in 5.0 seconds = 822.450 FPS
4051 frames in 5.0 seconds = 803.728 FPS
4120 frames in 5.0 seconds = 823.837 FPS
4133 frames in 5.0 seconds = 826.448 FPS

Is that OK or very bad?

---

### Post by NMUrugbysteve on 2006-09-12
I'd say those are pretty expectable rates for an i810.

---

### Post by blacktorch on 2006-09-12
OK, yeah well I guess they are. 

Anyway I installed wine 0.9.19, and Grid Wars worked for instance. But still not warcraft 3... now instead of that message it goes into fullscreen, a black one, then everything freezes...

---

### Post by noxxle on 2007-02-24
i have an intel 915gm card (i810 driver) and I get about 800 fps with glxgears in edgy and feisty. However, with mandriva 2006, i get 1400. I think think this is because mandriva 2006 used a 6.9 cvs xorg. I can no longer use mandriva 2006 because updates arent available, but i think when i updated the xorg within 2006 it then slowed down to about 800 fps

---

### Post by loko on 2007-03-07
i also can confirm that these i810-drivers are very slow....

tried a couple of apps, (google-earth) but it is really slow,

i hope this will be fixed till feisty is final

---

