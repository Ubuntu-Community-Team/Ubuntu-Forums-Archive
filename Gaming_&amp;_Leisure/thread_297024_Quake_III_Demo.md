---
title: "Quake III Demo"
date: 2006-11-10
forum: Gaming &amp; Leisure
---

### Post by transform100 on 2006-11-10
Hello i installed ubuntu and i like it but i can't get Quake III to start if i can't fix this i am switching back to windows

[HTML]Q3 1.11 linux-i386 Dec  4 1999
----- FS_Startup -----
Current search path:
/home/transform100/.q3a/baseq3
./baseq3

----------------------

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/transform100/.q3a/demoq3
./demoq3/pak0.pk3 (1387 files)
./demoq3

----------------------
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: candyman32
IP: 127.0.1.1
----- R_Init -----
...loading libGL.so: QGL_Init: Can't load libGL.so from /etc/ld.so.conf or current dir: libglide2x.so: cannot open shared object file: No such file or directoryfailed
...loading libMesaVoodooGL.so: QGL_Init: Can't load libMesaVoodooGL.so from /etc/ld.so.conf or current dir: libglide2x.so: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Error: GLimp_Init() - could not load OpenGL subsystem
[/HTML]

---

### Post by aidanr on 2006-11-10
did you install graphics drivers?

if you have and its still not working, try
```
sudo ln -s /usr/lib/libGL.so.1 /path/to/quake3/install/folder/libGL.so
```

i think by default the path is something like /usr/local/games/quake3

---

### Post by transform100 on 2006-11-10
I fixed it i had to do
[HTML]
sudo cd /usr/lib
ln -s libGL.so.1 libGL.so 
[/HTML]

---

