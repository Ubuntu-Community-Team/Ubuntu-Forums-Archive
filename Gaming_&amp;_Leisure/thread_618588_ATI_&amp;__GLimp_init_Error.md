---
title: "ATI &amp;  GLimp_init Error"
date: 2007-11-20
forum: Gaming &amp; Leisure
---

### Post by tenach on 2007-11-20
I have searched for an answer to this fruitlessly.  Yesterday I installed the latest ATI fglrx drivers from ati.amd.com with no problem and could play my games. Today however, I am getting an error with all but Neverwinter Nights (it is using it's own SDL library, not my machine's).  Unreal Tournament also runs fine as [stated on my site]("http://tlmservices.com/article/unreal-tournament-ubuntu").

I am using fglrx from ATI's site (ver. 8.42.3). Restricted Drivers Manager reports it as being in use.

Currently running Ubuntu 7.10 Gutsy Gibbon, 32-bit.

> tlm@Dral:~$ lspci|grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
tlm@Dral:~$ glxinfo|grep direct
direct rendering: Yes
tlm@Dral:~$ glxgears
9203 frames in 5.0 seconds = 1840.422 FPS


World of Padman:
> 
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) failed: No available video device
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

Nexuiz:
> 
Trying to load library... "libz.so.1" - loaded.
Compressed files support enabled
Added packfile /usr/share/games/nexuiz/data/data20070531.pk3 (3665 files)
Trying to load library... "libcurl.so.4" - loaded.
cURL support enabled
Initializing client
Quake Error: Failed to init SDL video subsystem: No available video device


SDL packages installed:
libsdl-1.2debian
libsdl-1.2debian-alsa
libsdl-1.2-dev

---

### Post by dopefish7590 on 2008-08-15
Yes, I know the age of the thread but...

I am getting this same error when I try to run Quake 3 Arena or anything else that uses SDL. Could anyone atleast give a hint to what is wrong? :(

---

