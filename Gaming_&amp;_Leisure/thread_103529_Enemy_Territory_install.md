---
title: "Enemy Territory install"
date: 2005-12-14
forum: Gaming &amp; Leisure
---

### Post by Hoop on 2005-12-14
I am trying to install enemy territory on ubuntu 5.10 AMD 64  I installed through 32 bit emulation ie . linux32 ./enemy-territory-install.run. Installation went ok although i did get a gdk message :

Gdk-WARNING **: locale not supported by Xlib, locale set to C

Gdk-WARNING **: can not set locale modifiers

But I've read in these forums that it's a minor bug with ubuntu and the software still runs. After install I tried to run both 'et' then 'linux32 et' both produced the same result :

Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: QGL_Init: dlopen libGL.so.1 failed: libXxf86vm.so.1: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem.

I have a Geforce 5500, I've installed the drivers and glxgears runs very smooth. I don't think its anything to do with that. I suspect it's a compatability between 64bit OS and 32bit Apps.  Can anyone help please ?
:(

---

### Post by Harleen on 2005-12-14
You don't seem to have libxxf86vm1 installed. It should be installed because several other packages depend on it. But try to intall it anyway for the case you haven't already.

---

### Post by Hoop on 2005-12-14
Thanks for reply, I did have it installed but I installed it again anyway ( can't hurt ) but still the same problem. I recompiled source as 64 bit too, seen as it was calling a 64bit Library file but still had exactly the same result . No ET for me. It's a shame cos I like ubuntu but ET comes first . Might have to switch OS's. I had it running on Gentoo 64 perfectly, less lag than Windows version and graphics card performed better but could only have KDE desktop, weird prob with sound on Gnome. If you or anyone else has got some Ideas , then I'd like to hear . Like I said, I do Like ubuntu. It's very easy to use.

---

