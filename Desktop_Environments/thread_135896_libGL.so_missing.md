---
title: "libGL.so missing?"
date: 2006-02-24
forum: Desktop Environments
---

### Post by deathbyswiftwind on 2006-02-24
Hey everyone I need some help. I did a fresh install of Ubuntu and installed the ati driver like always. Never had a problem before but now when I try to run my quake 3 I get this error.

rob@ubuntu:~$ sh /usr/local/games/quake3/quake3
Q3 1.11 linux-i386 Nov 24 1999
----- FS_Startup -----
Current search path:
/home/rob/.q3a/baseq3
./baseq3/pak0.pk3 (3539 files)
./baseq3

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
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntu
IP: 127.0.0.1
----- R_Init -----
...loading libGL.so: QGL_Init: Can't load libGL.so from /etc/ld.so.conf or current dir: /usr/local/games/quake3/libGL.so: cannot open shared object file: No such file or directory
failed
...loading libMesaVoodooGL.so: QGL_Init: Can't load libMesaVoodooGL.so from /etc/ld.so.conf or current dir: /usr/local/games/quake3/libMesaVoodooGL.so: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )

I dont know what went wrong my gl works on the gl screen savers but quake 3 refuses to run. Could someone please help

---

