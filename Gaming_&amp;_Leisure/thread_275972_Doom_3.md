---
title: "Doom 3"
date: 2006-10-12
forum: Gaming &amp; Leisure
---

### Post by dema on 2006-10-12
When trying to execute doom3 I get this error:

Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 1280x800
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 1280x800
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 38
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 42
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 43
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL


Can anyboy tell my why? I've allready installed drivers for my Nvidia card.

---

### Post by Naegling23 on 2006-10-12
looks like you dont have the correct resolutions enabled on your display.  Try setting up your monitor again, and manually add as many of the resolutions that your monitor/video card can support.  I had a similar problem with neverwinter nights, and that solved my problem.

---

### Post by dema on 2006-10-12
How can I change the resolution in Doom3?

---

### Post by Naegling23 on 2006-10-12
not in doom3, on your display.  check the xorg.conf file.

---

### Post by dema on 2006-10-13
I don't think thats the solution. I can allready play games like Enemy Terrority.

---

### Post by Naegling23 on 2006-10-13
it might not be, it might be.  I had a problem where I could play doom3, but not neverwinter nights.  Turns out that after inabling some resolutions I now can play both.  I have no idea why, its just one area that you might want to look into.

---

### Post by redbull_monsta on 2006-10-13
Are you using 24-bit colour Doom3 requires 24-bit 

16-bit or 32-bit dont work

look for the defaultdepth= in your /etc/X11/xorg.conf

---

