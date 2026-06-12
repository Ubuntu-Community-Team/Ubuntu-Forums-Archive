---
title: "[SOLVED] enemy territory - screen error"
date: 2008-01-10
forum: Gaming &amp; Leisure
---

### Post by depele on 2008-01-10
Hello, 

Just installed et + patches 

But since I am running gutsy I have this strange problem.

I start et like usual by typing et in a console or with the menu entry.

But then my screen flashes, It changes resolution and that's it.

Nothing more to see.
I reinstalled et already. 
Tried on another computer also with Linux.
Video drivers are installed.


Anyone an idea?

Thanks anyway.

Arne

---

### Post by Dogfighter on 2008-01-10
post the console output, maybe we can see something suspicous.

---

### Post by frodon on 2008-01-10
Details please, (terminal output, video card, ubuntu version 32bits or 64bits, ET 2.6 patch applied, 2.6d patch applied, using compiz,  ...)

The terminal output is in general useful to locate the problem.

---

### Post by depele on 2008-01-11
Output on the first computer.

```
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/depele/.etwolf/etmain/^dsaberpeakcamp6.pk3 (1 files)
/home/depele/.etwolf/etmain/z_fieldopsincompl.pk3 (16 files)
/home/depele/.etwolf/etmain/WTF_AXIS-INFANTARY.pk3 (170 files)
/home/depele/.etwolf/etmain/venice.pk3 (330 files)
/home/depele/.etwolf/etmain/toiletmanfinal.pk3 (72 files)
/home/depele/.etwolf/etmain/te_valhalla.pk3 (56 files)
/home/depele/.etwolf/etmain/temple_final.pk3 (57 files)
/home/depele/.etwolf/etmain/sw_oasis_b3.pk3 (45 files)
/home/depele/.etwolf/etmain/sw_goldrush_te.pk3 (48 files)
/home/depele/.etwolf/etmain/SG_1945_final.pk3 (217 files)
/home/depele/.etwolf/etmain/scripts.pk3 (2 files)
/home/depele/.etwolf/etmain/sado_campaign_93.pk3 (2 files)
/home/depele/.etwolf/etmain/sado_campaign_89.pk3 (2 files)
/home/depele/.etwolf/etmain/sado_campaign_87.pk3 (2 files)
/home/depele/.etwolf/etmain/rtcc2.pk3 (41 files)
/home/depele/.etwolf/etmain/Riverwar_V2.pk3 (102 files)
/home/depele/.etwolf/etmain/rhine2.pk3 (117 files)
/home/depele/.etwolf/etmain/resurrection.pk3 (305 files)
/home/depele/.etwolf/etmain/mp_sub_fal.pk3 (225 files)
/home/depele/.etwolf/etmain/mlb_beach.pk3 (97 files)
/home/depele/.etwolf/etmain/glider_251.pk3 (52 files)
/home/depele/.etwolf/etmain/fun_beach_final.pk3 (72 files)
/home/depele/.etwolf/etmain/Frostbite.pk3 (99 files)
/home/depele/.etwolf/etmain/Fragzone.pk3 (2 files)
/home/depele/.etwolf/etmain/flughafen.pk3 (355 files)
/home/depele/.etwolf/etmain/et_ice.pk3 (61 files)
/home/depele/.etwolf/etmain/ed2kr7.pk3 (2 files)
/home/depele/.etwolf/etmain/ckrotation8.pk3 (2 files)
/home/depele/.etwolf/etmain/campaigncycle1.pk3 (1 files)
/home/depele/.etwolf/etmain/caen.ba7c1ca4.pk3 (83 files)
/home/depele/.etwolf/etmain/bs-jay4.pk3 (1 files)
/home/depele/.etwolf/etmain/britishskins_v1.pk3 (79 files)
/home/depele/.etwolf/etmain/braundorf_b4.pk3 (51 files)
/home/depele/.etwolf/etmain/beach.pk3 (45 files)
/home/depele/.etwolf/etmain/beach.0a2b8329.pk3 (53 files)
/home/depele/.etwolf/etmain/baserace_b3a.pk3 (139 files)
/home/depele/.etwolf/etmain/axislab_final_sp1.pk3 (3 files)
/home/depele/.etwolf/etmain/axislab_final.pk3 (172 files)
/home/depele/.etwolf/etmain/arena0210.pk3 (11 files)
/home/depele/.etwolf/etmain/adlernest.pk3 (113 files)
/home/depele/.etwolf/etmain/1944_beach.pk3 (60 files)
/home/depele/.etwolf/etmain/10map.pk3 (1 files)
/home/depele/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
7127 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/de_pele/etconfig.cfg
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
XFree86-VidModeExtension Activated at 800x600
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XFree86-VidModeExtension Activated at 640x480
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
```


```
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)

```

I think it has something to do with my grapics card.
I just deinstalled compiz.

---

### Post by frodon on 2008-01-11
We need also other details, ubuntu version, kernel, graphic drivers, compiz or not and so on. Without details we won't be able to help you.

First read of your log seems to show a problem with your ATI graphic drivers and openGL.

---

### Post by depele on 2008-01-11
```
depele@cyberlinux:~$ uname -r
2.6.22-14-generic

```

no restricted drivers needed. (this is what ubuntu tells me)

I removed compiz 
(apt-get remove compiz)

graphics driver: I have no idea.

---

### Post by frodon on 2008-01-11
Check if you have currently direct rendering capabilities (mandatory for ET) :
```
glxinfo | grep direct
```The command above should tell you if you have direct rendering or not.

If the answer is no check in synaptic if you have the xserver-xgl package installed, if yes this is the reason of your problem. In this case just uninstall this package, the drawback will be that you won't be able to activate desktop effect anymore as xserver-xgl package is required for ATI cards if you wish to activate compiz.

---

### Post by depele on 2008-01-11
Just installed xserver-xgl package.

Still getting this error in server console.

```
Using XFree86-VidModeExtension Version 2.2
XFree86-VidModeExtension Activated at 800x600
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XFree86-VidModeExtension Activated at 640x480
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
.
```

Is it possible ubuntu changes video driver by installing software like beryl, compiz?

---

### Post by frodon on 2008-01-11
I said to uninstall it if installed not to install it ;)

---

### Post by depele on 2008-01-12
Sorry 
terrible mistake.
I'll try it out as soon as I get home.

---

### Post by depele on 2008-01-15
uninstalled xorg-server-xgl package

output console
```
XFree86-VidModeExtension Activated at 800x600
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XFree86-VidModeExtension Activated at 640x480
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
```

---

### Post by frodon on 2008-01-15
And what is the out put of :
```
glxinfo | grep direct
```

---

### Post by depele on 2008-01-15
I am first going to fix my xserver 

I have no visual no more.

I'll be back when it is fixed.

---

### Post by depele on 2008-01-16
ok since we have visual again. 
the output of glxinfo | grep direct

```
glxinfo | grep direct
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual
depele@cyberlinux:~$ 

```

---

### Post by frodon on 2008-01-16
Ok the problem come from your configuration not from ET. Post here you xorg.conf file (it's in /etc/X11/) and try to install your graphic card drivers if not already done.

---

### Post by depele on 2008-01-18
ffft! 
this problem opened my eyes for a lot other problems,
I had messed around to much with my dist.

So It is going to be a format

Thanks anyway.

---

### Post by depele on 2008-01-19
Just reinstalled gusty.

One strange thing.
Compiz is working
and
et is working.


Anyway. 
Thanks for your help

---

