---
title: "quake 4 ~ SDL_init failed"
date: 2005-10-21
forum: Gaming &amp; Leisure
---

### Post by _jB on 2005-10-21
> --------------- R_InitOpenGL ----------------
Initializing SDL subsystem
TODO: Sys_SetClipboardData
********************
ERROR: SDL_Init failed: No available video device

********************
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: SDL_Init failed: No available video device

> jb@ubu:~$ sdl-config --version
1.2.9

any ideas :confused:

---

### Post by _jB on 2005-10-21
Oki, i'll go kick my self now.. Needed the xorg-dev thingy..
#DSL: ./configure --with-x
worked fine ;)

But now i'm getting a **ERROR: couldn't find game dynamic library** instead.

Guess i'll have to keep trying ;)

---

