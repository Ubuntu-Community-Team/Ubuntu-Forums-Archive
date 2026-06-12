---
title: "quake 4 can't find libGL.so.1"
date: 2011-08-05
forum: Gaming &amp; Leisure
---

### Post by keelx on 2011-08-05
Whenever I run quake 4 (or prey or doom 3) I get this error or something similar:


```
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
TODO: Sys_SetClipboardData
********************
ERROR: SDL_GL_LoadLibrary libGL.so.1 failed: Failed loading libGL.so.1

********************
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: SDL_GL_LoadLibrary libGL.so.1 failed: Failed loading libGL.so.1
```

When I know for a fact libGL.so.1 is in /usr/lib

And I read somewhere that LD_PRELOAD=libGL.so.1 will solve the problem, but then, on all games, they don't even load and I just get this:
```
./quake4.x86: libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/i386-linux-gnu/libstdc++.so.6)
```

But I do have gcc 4.5.2, from the buld-essential package.

I also have the correct drivers for my card and such, running glxgears runs at about 600-700fps.

How do I solve this? Thanks in advance.

---

### Post by Furball588 on 2011-08-05
but it looks like it's looking for SDL too...

---

### Post by keelx on 2011-08-05
> **Furball588 said:**
> but it looks like it's looking for SDL too...

I have SDL installed. And what in that error would make you think that? It said that SDL couldn't load the libGL.so.1 library, not that it couldn't find SDL itself.

---

### Post by ruffEdgz on 2011-08-05
Just curious, when you run these commands, does anything come up?
```

sudo updatedb

sudo locate libgcc_s.so.1

```

Are you running the 64bit or 32bit version of Ubuntu?

Cheers!

---

### Post by fdrake on 2011-08-05
? 
```
sudo apt-get install libgcc1
```

---

### Post by keelx on 2011-08-05
> **ruffEdgz said:**
> Just curious, when you run these commands, does anything come up?
```

sudo updatedb

sudo locate libgcc_s.so.1

```

Are you running the 64bit or 32bit version of Ubuntu?

Cheers!
32-bit.
sudo updatedb prints nothing.
sudo locate libgcc_s.so.1 prints this:
```
/home/hoodwink/prey-demo/libgcc_s.so.1
/home/hoodwink/quake4-demo/libgcc_s.so.1
/lib/i386-linux-gnu/libgcc_s.so.1
/lib64/libgcc_s.so.1
/usr/lib/libgcc_s.so.1
/usr/local/games/doom3-demo/libgcc_s.so.1
```

---

### Post by keelx on 2011-08-05
> **fdrake said:**
> ? 
```
sudo apt-get install libgcc1
```

libgcc1 is already the newest version.

---

### Post by keelx on 2011-08-05
I found that if I just run the .x86 file, rather than the script, it opens and plays. Just one problem with that though- it can't find any of the textures whatsoever. I am just walking around in this solid grey world. Not really playable...

---

### Post by ruffEdgz on 2011-08-05
I think this part is interesting and maybe can be looked into?
```

/lib64/libgcc_s.so.1

```
If you have a 32bit OS, why have /lib64 (that directory is usually a symbolic link to lib when using a 64bit OS)?

Type in this to see what kind of OS you have (just want to verify):
```

uname -a | awk '{print $12}'

```

Also, I have the libgcc1 installed on my computer (using 64bit) and found it here:
```

/lib/libgcc_s.so.1

```

Hope this helps.

---

### Post by keelx on 2011-08-05
> **ruffEdgz said:**
> I think this part is interesting and maybe can be looked into?
```

/lib64/libgcc_s.so.1

```
If you have a 32bit OS, why have /lib64 (that directory is usually a symbolic link to lib when using a 64bit OS)?

Type in this to see what kind of OS you have (just want to verify):
```

uname -a | awk '{print $12}'

```

Also, I have the libgcc1 installed on my computer (using 64bit) and found it here:
```

/lib/libgcc_s.so.1

```

Hope this helps.

I have the libgcc_s.so.1 in my usr/lib directory as well.

```
uname -a | awk '{print $12}'
i686

```

---

### Post by Brebs on 2011-08-07
*How* are you running quake4?

This is my startup script:
```
# To stop mouse being ultra-fast in menus
export SDL_VIDEO_X11_DGAMOUSE=0

cd /opt/quake4
export LD_LIBRARY_PATH="/opt/quake4:${LD_LIBRARY_PATH}"
./quake4smp.x86 "$@"
```
Notice that *export* command, so it uses quake4's *libSDL-1.2.id.so.0* which is in /opt/quake4/

Also notice that I'm using the SMP executable.

---

