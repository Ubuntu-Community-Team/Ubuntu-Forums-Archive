---
title: "Enemy territory installed but won't start please help"
date: 2007-06-02
forum: Gaming &amp; Leisure
---

### Post by Shadowmeph on 2007-06-02
ok I only have about 3 days experience with linux but I am learning.
Anyway, I was having a problem installing game but now that I have the game installed I have run into a new problem which is that when I try to run the game it starts for a second then goes back to desk top this is what show up on the terminal;

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/meph/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
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
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect

not sure whats up with that or what it all means my system =3.4 ghz, 1.5gig ram /ati x800 video card,sound blaster live5.1 sound card and the os is feisty fawn I hope that this is enough information to help

---

### Post by B0rsuk on 2007-06-02
I'm 95% sure you don't have hardware acceleration enabled. With nvidia drivers it's as simple as installing *nvidia-glx* package and using one command to enable it. ATI drivers are much worse. 
Maybe someone else can help you, but now you know what to look for. Search the forum or [http://wiki.ubuntu.com](http://wiki.ubuntu.com)

---

### Post by Shadowmeph on 2007-06-02
> **B0rsuk said:**
> I'm 95% sure you don't have hardware acceleration enabled. With nvidia drivers it's as simple as installing *nvidia-glx* package and using one command to enable it. ATI drivers are much worse. 
Maybe someone else can help you, but now you know what to look for. Search the forum or [http://wiki.ubuntu.com](http://wiki.ubuntu.com)
well you where right about the hardware acceleration enabled it is now rebooted but still am having same error thank you but it still is the same :) .

---

