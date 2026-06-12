---
title: "Lost compiz on Lucid with Intel HD Graphics"
date: 2010-07-23
forum: Desktop Environments
---

### Post by immerohnegott on 2010-07-23
I honestly have no clue how this happened, but compiz now refuses to start. I discovered that somehow GLX had been uninstalled and replaced by SWX (the software rasterizer - this gives Brian Paul as the OpenGL/GLX server vendor strings). Reinstalled GLX, currently have Direct Rendering and the proper vendor strings (SGI and Tungsten, I believe).

Still nothing. OpenGL seems to be working fine, as Nexuiz runs pretty well.

I tried running compiz --replace from the terminal to get any errors, but it just spits out "Falling back to default window manager", without so much as a hex code to tell me why.

Any ideas?

--------Update---------

Ran compiz --debug --replace to see if I could get anything else. It gives the following:

> taintsauce@the-****ing-fury:~$ compiz --replace --debug
compiz (core) - Debug: Could not stat() file /home/taintsauce/.compiz/plugins/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/taintsauce/.compiz/plugins/libccp.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/taintsauce/.compiz/plugins/libmove.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/taintsauce/.compiz/plugins/libresize.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/taintsauce/.compiz/plugins/libplace.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/taintsauce/.compiz/plugins/libdecoration.so : No such file or directory

Launching fallback window manager


Tried reinstalling all compiz related packages, to no avail.

---

### Post by aleixsr on 2010-11-27
> **immerohnegott said:**
> I honestly have no clue how this happened, but compiz now refuses to start. I discovered that somehow GLX had been uninstalled and replaced by SWX (the software rasterizer - this gives Brian Paul as the OpenGL/GLX server vendor strings). Reinstalled GLX, currently have Direct Rendering and the proper vendor strings (SGI and Tungsten, I believe).

Still nothing. OpenGL seems to be working fine, as Nexuiz runs pretty well.

I tried running compiz --replace from the terminal to get any errors, but it just spits out "Falling back to default window manager", without so much as a hex code to tell me why.

Any ideas?

--------Update---------

Ran compiz --debug --replace to see if I could get anything else. It gives the following:



Tried reinstalling all compiz related packages, to no avail.

Same problem here, any way to solve it?

---

