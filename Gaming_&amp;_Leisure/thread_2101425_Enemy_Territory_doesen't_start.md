---
title: "Enemy Territory doesen't start"
date: 2013-01-04
forum: Gaming &amp; Leisure
---

### Post by linuxsyst on 2013-01-04
Hello, 
I added the playdeb repository and installed the game but when i try to open the game it does nothing it makes the .etwolf folder but it doesn’t start the game.

---

### Post by mentorious on 2013-01-04
type in  terminal:

```
enemy-territory
```

and paste output here (via e.g. pastebin)

---

### Post by linuxsyst on 2013-01-05
```
admin@blackhat:~$ enemy-territory
enemy-territory: command not found

```
I have the icon in the menu though and I tried to reinstall it doesn&#8217;t help

---

### Post by mentorious on 2013-01-05
Sorry, my mistake..  I didn't play for long time and I forget the command.

type this:

```
et
```

---

### Post by linuxsyst on 2013-01-05
```
admin@blackhat:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/admin/.etwolf/etmain
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
...loading libGL.so.1: QGL_Init: dlopen libGL.so.1 failed: libGL.so.1: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```

---

### Post by linuxsyst on 2013-01-05
Thanks, 
I found a soultion - > sudo apt-get install ia32-libs

---

