---
title: "Have 3d acceleration, but games cannot load libGL.so.1"
date: 2009-05-31
forum: General Help
---

### Post by Polygon on 2009-05-31
Like the post says, i have 3d acceleration:

```
mark@Humboldti:~/games/prey$ glxinfo | grep direct
direct rendering: Yes
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
mark@Humboldti:~/games/prey$ 
```

but i cannot play any game or anything that requires 3d acceleration:

```
----- R_InitOpenGL -----
Setup SDL display connection
Initializing OpenGL display
Loading GL driver '(default)' through SDL
WARNING: SDL_GL_LoadLibrary (null) failed: Failed loading libGL.so.1

Setup SDL display connection
Initializing OpenGL display
Loading GL driver '(default)' through SDL
WARNING: SDL_GL_LoadLibrary (null) failed: Failed loading libGL.so.1

idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL

```

I am using the 185.18.14 nvidia drivers from their website, and i have tried uninstalling and reinstalling them at least 3 times, and it doesn't seem to work.

I have a 9800 gtx also.

---

### Post by Keith Hedger on 2009-05-31
the lib you are looking for can be found in these packages:
libgl1-mesa-glx
libgl1-mesa-swx11
nvidia-glx-173
amongst others and can be installed by installing one of them from the repos.

---

### Post by Polygon on 2009-05-31
The file is there, its just that the games are refusing to load it for some reason.

```
mark@Humboldti:~/games/prey$ ls /usr/lib | grep libGL
libGLcore.so.1
libGLcore.so.185.18.14
libGLEW.so.1.5
libGLEW.so.1.5.0
libGL.la
libGL.so
**_libGL.so.1_**
libGL.so.185.18.14
libGLU.a
libGLU.so
libGLU.so.1
libGLU.so.1.3.070300
mark@Humboldti:~/games/prey$ 

```

---

### Post by Keith Hedger on 2009-05-31
What games exactly? as I just ran up vega strike and it loaded fine

---

### Post by Polygon on 2009-05-31
Right now, the blender COMPILER (the regular program works fine) doesn't run, along with  prey, enemy territory quake wars, doom 3, quake 4 demo, Nexuiz, etc

---

### Post by OliW on 2010-02-13
Did you have any luck with this?

I found that things worked perfectly while I was using the Ubuntu version of the binary driver but when I upgraded to the 195 beta on nvidia's website, 3D still worked but games (including the ones you listed) throw this error.

I'd rather stay using the beta driver but I'd also like my games back =(

---

### Post by bhencetotozo on 2010-02-13
> **Polygon said:**
> Like the post says, i have 3d acceleration:

```
mark@Humboldti:~/games/prey$ glxinfo | grep direct
direct rendering: Yes
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
mark@Humboldti:~/games/prey$ 
```

but i cannot play any game or anything that requires 3d acceleration:

```
----- R_InitOpenGL -----
Setup SDL display connection
Initializing OpenGL display
Loading GL driver '(default)' through SDL
WARNING: SDL_GL_LoadLibrary (null) failed: Failed loading libGL.so.1

Setup SDL display connection
Initializing OpenGL display
Loading GL driver '(default)' through SDL
WARNING: SDL_GL_LoadLibrary (null) failed: Failed loading libGL.so.1

idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL

```

I am using the 185.18.14 nvidia drivers from their website, and i have tried uninstalling and reinstalling them at least 3 times, and it doesn't seem to work.

I have a 9800 gtx also.

Are you having problems with cedega?

Driver 195 BETA is AWESOME !!!! i wish i knew about it's existance before !!! It is PERFECT ! [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)


-----------------------------------------------------
How I did it: (make sure to use SU not sudo)
1) Control+ALT+F1
2) sudo /etc/init.d/gdm stop
3) cd Desktop
4) su (sudo did not let it work, so I did SU)
5) password (password for su (root))
6) sh ./NVIDIA-Linux-x86-195.36.03-pkg0.run
-----------------------------------------------------
My Video Card : Nvidia Gforce 7950 GX2
My personal Driver Rating for my video card.
100% good. Version 195
70% good. Version 173
60% good Version 96
40% good Version 185
Tested and measured by EYE.(no software used I mesured by EYE experience)
-----------------------------------------------------

---

