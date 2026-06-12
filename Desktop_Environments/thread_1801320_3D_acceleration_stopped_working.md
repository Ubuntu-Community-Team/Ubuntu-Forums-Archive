---
title: "3D acceleration stopped working"
date: 2011-07-10
forum: Desktop Environments
---

### Post by Lars Pensjö on 2011-07-10
There was an automatic update, which may be the reason. The symptoms are:

[LIST=1]
[*]Trying to start an OpenGL application, I got the error message "No GLXFBConfigs returned".
[*]I rebooted. When logging in, I got the message that Unity is no longer supported, and got the old desktop look instead.
[*]Opening "Additional drivers", it lists "NVIDIA accelerated graphics driver" as "activated but not in use".
[/LIST]

The following test seems to confirm the problems?

[INDENT][FONT="Courier New"]> ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 11.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G86M [Quadro NVS 135M] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 
[/FONT][/INDENT]

It is a DELL laptop.

---

### Post by Lars Pensjö on 2011-07-10
I did a re-install of Ubuntu, and the OpenGL 3D now works again.

Strange though, the "Additional drivers" still report no proprietary drivers are in use in this system, even when I have an OpenGL program that reports:

[FONT="Courier New"]Vendor: NVIDIA Corporation
Renderer: Quadro NVS 135M/PCI/SSE2
Version: 3.3.0 NVIDIA 270.41.06
GLSL: 3.30 NVIDIA via Cg compiler
[/FONT]

Edit: the script [compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check") now reports OK on all tests.

---

### Post by wildmanne39 on 2011-07-10
> **Lars Pensjö said:**
> I did a re-install of Ubuntu, and the OpenGL 3D now works again.

Strange though, the "Additional drivers" still report no proprietary drivers are in use in this system, even when I have an OpenGL program that reports:

[FONT=Courier New]Vendor: NVIDIA Corporation
Renderer: Quadro NVS 135M/PCI/SSE2
Version: 3.3.0 NVIDIA 270.41.06
GLSL: 3.30 NVIDIA via Cg compiler
[/FONT]

Edit: the script [compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check") now reports OK on all tests.Hi, that part about it not being in use is just a bug it really is in use if you activated it and you can see the green dots in additional drivers. Plus you could not get to the unity desktop if it was not activated and in use.

---

