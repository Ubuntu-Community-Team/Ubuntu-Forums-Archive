---
title: "Quake 4 1.3-2 will not run"
date: 2006-11-11
forum: Gaming &amp; Leisure
---

### Post by shawn on 2006-11-11
I can't get Quake 4 to run on my system. I get this error when i try to run it:

```
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
WARNING: SDL_Init failed: No available video device

Initializing SDL subsystem
WARNING: SDL_Init failed: No available video device

--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL

```

I searched google and tried a few things. I have my desktop set at 24bpp and "libsdl1.2debian-alsa" is installed. I also edited the quake4 start up script to load libGL.so.1 like this:

```
/usr#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/home/shawn/Games/quake4/"
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:."
LD_PRELOAD=/usr/lib/libGL.so.1
export LD_PRELOAD
exec ./quake4.x86 "$@"

```

But nothing seems to work. The strange thing is that I was playing the demo a week or two ago and it ran fine.

Any ideas?

---

### Post by fng on 2006-11-11
Is direct rendering initialized?

```

fng@butters:~$ glxinfo | grep "direct rendering"
direct rendering: Yes
fng@butters:~$ 

```

---

### Post by shawn on 2006-11-11
Yep, the drivers are installed correctly and direct rendering is enabled. All the other games I have run without problems (Quake 1, Quake 3, Enemy Territory, Neverwinter Nights and Glest).

EDIT: I just tried Quake 4 1.2 and the same problem occurs.

---

### Post by Fireman_DJ on 2007-12-19
I have a similar issue trying to run Xmoto. It ran before and now has stopped working.
Enemy Territory still works fine.

And I have SDL installed, direct rendering working etc.

> dj@main:~$ xmoto
fatal exception : (2) SDL_Init : No available video device

---

### Post by Fireman_DJ on 2008-01-13
Nobody can help?

---

### Post by Sockerdrickan on 2008-01-13
Get your driver configured maybe... Do you have one installed for graphics(3D) at all?

---

### Post by Fireman_DJ on 2008-01-13
I sure hope so, otherwise how could I have just been playing Enemy Territory, a 3D first person shooter game.

It's only programs that rely on SDL that fail to work.

---

### Post by Sockerdrickan on 2008-01-13
[www.libsdl.org](www.libsdl.org) compile the latest version and install, and you might have fixed your problem!

---

### Post by Fireman_DJ on 2008-01-14
I did that a while back for v1.2.12.
I've now done it again for v1.2.13 with the same results.

---

