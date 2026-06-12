---
title: "World of Padman Errors!"
date: 2011-01-09
forum: Gaming &amp; Leisure
---

### Post by Maverick_Hunter on 2011-01-09
Everytime I try to run WorldofPadman, I get this error 


nomadd@Freedom:~$ worldofpadman
WoP 1.5  (ioq3 r1553) linux-i386 Dec 29 2010
----- FS_Startup -----
Current search path:
/home/nomadd/.padman/wop
/usr/share/games/worldofpadman/wop/wop_005.pk3 (3224 files)
/usr/share/games/worldofpadman/wop/wop_004.pk3 (798 files)
/usr/share/games/worldofpadman/wop/wop_003.pk3 (296 files)
/usr/share/games/worldofpadman/wop/wop_002.pk3 (1903 files)
/usr/share/games/worldofpadman/wop/wop_001.pk3 (534 files)
/usr/share/games/worldofpadman/wop

----------------------
6755 files in pk3 files
execing default.cfg
couldn't exec wopconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read wophistory.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.779
...setting mode 2: 1024 768
Available modes: '1366x768 1360x768 640x480 800x600 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (2)
Initializing OpenGL display
...setting mode 2: 1024 768
Available modes: '1366x768 1360x768 640x480 800x600 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (2)
Setting r_mode 2 failed, falling back on r_mode 0
Initializing OpenGL display
...setting mode 0: 640 480
Available modes: '1366x768 1360x768 640x480 800x600 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (0)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
GLimp_Init() - could not load OpenGL subsystem


It runs decent-ish in WINE. but I can't get the native linux version to run please help!

I'm running a HP G60535-DX Ubuntu 10.10

---

### Post by Synapsi on 2011-01-16
Yea, getting the same problem, for Wolfenstein Enemy Territory, as well as assault cube.

---

### Post by Perfect Storm on 2011-01-16
> setting mode 2: 1024 768
It's trying to start up in resolution 1024x768
Do your screen support this resolution?

You can properly change the resolution in World of Padman ini file. Try check your home directory (you have to set nautilus to see hidden files first).

---

### Post by Gilbert Gosseyn III on 2011-03-06
I also have the same problem, though I'm pretty sure my screen supports this resolution. This is my output: 


WoP 1.5  (ioq3 r1553) linux-i386 Dec 29 2010
----- FS_Startup -----
Current search path:
/home/username/.padman/wop
/usr/share/games/worldofpadman/wop/wop_005.pk3 (3224 files)
/usr/share/games/worldofpadman/wop/wop_004.pk3 (798 files)
/usr/share/games/worldofpadman/wop/wop_003.pk3 (296 files)
/usr/share/games/worldofpadman/wop/wop_002.pk3 (1903 files)
/usr/share/games/worldofpadman/wop/wop_001.pk3 (534 files)
/usr/share/games/worldofpadman/wop

----------------------
6755 files in pk3 files
execing default.cfg
couldn't exec wopconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read wophistory.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.600
...setting mode 2: 1024 768
Available modes: '1280x800 640x480 800x600 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (2)
Initializing OpenGL display
...setting mode 2: 1024 768
Available modes: '1280x800 640x480 800x600 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (2)
Setting r_mode 2 failed, falling back on r_mode 0
Initializing OpenGL display
...setting mode 0: 640 480
Available modes: '1280x800 640x480 800x600 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (0)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
GLimp_Init() - could not load OpenGL subsystem


I'm using 10.04 LTS on an Acer Extensa 5230E 
Sorry but I can't find any .ini file related in any way to worldofpadman. 

Also, when I type in a terminal worldofpadman -h (or --help) it gives me the following output: 

/usr/games/worldofpadman: 26: Bad substitution

It seems like the program (or the client) does not recognize its own syntax. 

Could the problem be related to one of the following? 
- missing drivers 
- giving one or more files administrator privileges or using chmod (but I also tried with a sudo) 
- setting screen resolution (how? since there's no .ini file available and there's no way giving outputs such as --r_mode since every possible option gives a syntax error)

---

### Post by rizzeh on 2011-03-07
create new file called autoexec.cfg in /home/.wop (if i remember correctly, ill double check once im at home), stick the below in it, changing the resolution to one that's supported by your monitor.
```

seta r_mode "-1"
seta r_customHeight "1080"
seta r_customWidth "1680"

```

---

### Post by Gilbert Gosseyn III on 2011-03-07
Unfortunately I still get the same error. I also tried with different resolutions and also giving different values to seta r_mode (ranged from 0 to 2). 

The strange part is, my computer fully supports 1280x800 screen resolution and lower, I normally run Sauerbraten with that. 

Someone suggested to patch the game to 1.5.1... but I have that version and nothing changed so far.

---

### Post by leeezly on 2011-03-13
I got the same problem. I have tried WOP on three different systems, two were 64bit. All three had different graphic processors and different screen solutions. All three came up with the same messages. This must be a problem on the developers or package maintainer side.

I have tried to get access to WOP Forum, but my account was never activated, so I couldn't ask the question over there.

What to do?

---

### Post by leeezly on 2011-03-28
Update:

The problem seems to be with Intel graphics. I was able to get it running with Nvidia. Due to a hint in the WoP forum it now also runs with Intel. The necessary setting in ~/.padman/wop/wopconfig.cfg is the following:

```

seta r_ext_multisample "0"
```

As well you might also the following helpful:

```

seta r_mode "-1"
seta r_depthbits "24"
seta r_customHeight "800"
seta r_customWidth "1280"
```

Good luck. :-)

---

### Post by lee8oi on 2011-06-22
> **leeezly said:**
> Update:

The problem seems to be with Intel graphics. I was able to get it running with Nvidia. Due to a hint in the WoP forum it now also runs with Intel. The necessary setting in ~/.padman/wop/wopconfig.cfg is the following:

```

seta r_ext_multisample "0"
```As well you might also the following helpful:

```

seta r_mode "-1"
seta r_depthbits "24"
seta r_customHeight "800"
seta r_customWidth "1280"
```Good luck. :-)



Bless you my friend! this fixed my problem with running padman on my dell inspiron 1525! had to create the wopconfig.cfg file, and add those entries but it worked. Thanks man!

---

