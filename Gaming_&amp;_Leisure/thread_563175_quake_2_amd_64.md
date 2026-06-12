---
title: "quake 2 amd 64"
date: 2007-09-29
forum: Gaming &amp; Leisure
---

### Post by Luksion Knight on 2007-09-29
Quake 2 will not work on my computer. i've read and done all the installation guides, but it never works. is there a way to get it working on a 64-bit system?

---

### Post by Cappy on 2007-09-29
```
sudo apt-get install quake2
```

You are supposed to copy over your CD data files somewhere (it probably says when you install that).

No one can help you without a link to your guides or what specifically isn't working.

---

### Post by reset3x on 2007-09-29
Install quake 2 via synaptic/adept or apt-get....


Copy your PAK files to /usr/share/games/quake2/baseq2/... Also they have to be renamed in lower case....


Also you can edit the quake2 script in /usr/local/bin/  to

 ```
#!/bin/bash
exec /usr/lib/games/quake2/quake2.real "$@"
*) exit 1
esac

```

This will rid you of the security warning you get when you start quake2...

EDIT:

Also I've found that using sdl instead of opengl will give you full screen... opengl full screen doesn't seem to work....

Good Luck!!!

---

### Post by Luksion Knight on 2007-09-30
how do i launch it in sdl? it says it cant load the demo and its shuting down. any exact explicit instructions as to what exact files i need for a full game install?

---

### Post by reset3x on 2007-09-30
Oh I assumed you have the retail game... If you have the retail game copy the PAK (pak0.pak. pak1.pak, pak2.pak) files from your CD to/usr/share/games/quake2/baseq2. You can select sdl in the video options after you start the game...

---

### Post by Luksion Knight on 2007-09-30
ok i have those pak files in the folder, but it says it cant load this one demo video (demo/dm2.dm) and its shutting down. how do i fix this?

---

### Post by Luksion Knight on 2007-09-30
the window that it opens in has no video, its just multicolored lines. after hitting enter and moving the arrow keys, i will get some terminal activity, but then it just tells me it cant load the map.

```
QuakeIIForge 0.3
Added packfile /usr/share/games/quake2/baseq2/pak0.pak (1106 files)
Added packfile /usr/share/games/quake2/baseq2/pak1.pak (279 files)
Added packfile /usr/share/games/quake2/baseq2/pak2.pak (2 files)
using /home/linkous/.quake2/baseq2/ for writing
Added packfile /home/linkous/.quake2/baseq2/pak0.pak (1106 files)
Added packfile /home/linkous/.quake2/baseq2/pak1.pak (279 files)
Added packfile /home/linkous/.quake2/baseq2/pak2.pak (2 files)
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
setting mode 3: 640 480
1488k surface cache
ref_soft version: SOFT 0.01
------------------------------------
CDAudio_Init: open of "/dev/cdrom" failed (123)
------- Loading game.so -------
==== InitGame ====
------- Server Initialization -------
0 entities inhibited
0 teams with 0 entities
-------------------------------------
====== Quake2 Initialized ======

0.0.0.0:0: client_connect
------- Server Initialization -------
0 entities inhibited
0 teams with 0 entities
-------------------------------------

Changing map...
reconnecting...
********************
ERROR: Couldn't open demos/demo1.dm2

********************
==== ShutdownGame ====
n
------- Loading game.so -------
==== InitGame ====
------- Server Initialization -------
0 entities inhibited
0 teams with 0 entities
-------------------------------------
0.0.0.0:0: client_connect
------- Server Initialization -------
********************
ERROR: Couldn't load maps/base1.bsp
********************
==== ShutdownGame ====
recursive shutdown
linkous@linkous-desktop:~/.quake2$ n
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-multiverse.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/amd64-universe.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/amd64-multiverse.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/amd64-main.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-universe.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/amd64-restricted.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-restricted.db (2, 'No such file or directory')
Unable to open binary database %s: %s /usr/share/command-not-found/programs.d/all-main.db (2, 'No such file or directory')
bash: n: command not found
```

---

### Post by reset3x on 2007-09-30
OK I see you've installed Quake2 Forge.. if you installed quake2 via synaptic you just need to type quake2 in the cli... If you installed by some other means I can't help you...

Sorry...

EDIT: Just another thought if you've installed to your home dir set the permissions for your account.. If you've installed elsewhere ensure the PAK file permissions are set to root....

---

