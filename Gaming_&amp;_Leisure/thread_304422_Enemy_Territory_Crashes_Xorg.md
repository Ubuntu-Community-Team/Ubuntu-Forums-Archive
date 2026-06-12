---
title: "Enemy Territory Crashes Xorg"
date: 2006-11-21
forum: Gaming &amp; Leisure
---

### Post by Ademan on 2006-11-21
Hi, I've recently installed wolfenstein: enemy territory (via that disgusting binary installer)  And when i go to run it, Xorg seems to crash and then i end up at the gdm login screen.

Now I saw this bug in the forums, but they all said the reason was that enemy territory was trying to initialize with a resolution higher than the desktop resolution, unfortunately for me, that's definitely not the case.  The highest resolution in my xorg.conf is 1920x1200 and that's the resolution my desktop is at.   I managed to get a dump of the console with "et > etdump.txt 2>&1"   here are the contents:

```
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/dan/.etwolf/etmain
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
Received signal 1, exiting...
```

I don't know what's going on, since that's kinda the opposite of the bug described before.  That's a considerably lower resolution than my desktop resolution.

If it helps at all, it appears i'm running at 50hz as opposed to 60 (its a laptop lcd which MAY explain the 50)

cheers
-Dan

---

### Post by seethru on 2006-11-21
glxinfo works fine?

---

### Post by Ademan on 2006-11-22
Of course, so does glxgears, counter strike, day of defeat source, day of defeat, half life (all under WINE).  As well as ut2k4 native , beryl.  Basically everything BUT enemy territory.  (i also tried true combat: elite which uses the enemy territory engine, both have the same problem.

cheers
-Dan

---

### Post by sanone on 2006-11-22
I have the same problem with "True Combat: Elite" on my notebook with the latest version of the nvidia drivers. Please try if the game works in window mode...

I can for instance run Sam & Max Episode 1 (windows game using wine) in windowed mode it works fine.

It all worked fine with the previous version of the nvidia drivers (the one in the edgy repo right now).

Hope this helps..
San.

---

### Post by Ademan on 2006-11-23
I'd love to try it, but unfortunately i don't know how to run the game in windowed mode.  (i'm using the linux native versions of wolfenstein and true combat)

Is there a command line option? or maybe a config option?

thanks
-Dan

---

### Post by sanone on 2006-11-23
I just tried and it seems to work in windowed mode. To enable this just edit the configuration file (I don't know the command line parameters either).

For True Combat: Elite I (g)edited this file "~/.etwolf/tcetest/profiles/your-profile-name/etconfig.cfg" and changed the line 
```
seta r_fullscreen "1"
```
to 
```
seta r_fullscreen "0"
```

Now it works here.. If I only could find a way to speed up this compiz thingie I would be a happy fragger once again ;)

Anyways, good luck!
San.

---

### Post by Ademan on 2006-11-23
Interestingly enough, .etwolf is owned by root and no one else has permissions to it.  (I installed as root)  Is there an install log somewhere so i can uninstall this game and start again?

(Oh, and NOTHING else is in it, which may be a problem haha)

cheers
-Dan

---

### Post by simplyw00x on 2006-11-23
sudo chmod ademan:ademan ~/.etwolf

(here I assume your username is ademan)

---

### Post by Ademan on 2006-11-24
Right, but unfortunately nothing is IN .etwolf.  So its really kinda useless to me right?

---

### Post by simplyw00x on 2006-11-24
No, as long as that dir is writable things should improve. Maybe.

---

### Post by Devilotx on 2006-12-12
I'm in the same position, My X server crashes to a red screen then X reboots, I've chowned the ~/.etwof directory for me, and I get nothing.

can you start the game windowed from a cli argument?

IE et -w or something

---

