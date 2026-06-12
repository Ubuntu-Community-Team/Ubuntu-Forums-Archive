---
title: "3D Problem"
date: 2005-08-27
forum: Gaming &amp; Leisure
---

### Post by rdh002 on 2005-08-27
First I am a noob. Not a programer. I have read the starter guide and can not find the answer to this problem.
I am trying to set up video to run Et. I have 3d enabled but get this error when I try to run the game. 

Help please!!

ome/dad/.etwolf/etmain
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
...loading libGL.so.1: Received signal 11, exiting...

---

### Post by brk3 on 2005-08-27
Are there no more error lines after the last one?

---

### Post by rdh002 on 2005-08-27
[QUOTE=brk3]Are there no more error lines after the last one?[/QUOTE]
 Nope thats it

---

### Post by brk3 on 2005-08-27
Do you have any other 3d accelerated games you can try? Do they work?

---

### Post by rdh002 on 2005-08-27
[QUOTE=brk3]Do you have any other 3d accelerated games you can try? Do they work?[/QUOTE]
 No I don't I just loaded Ubuntu and this was the first attept at any game. I do not have any other Linux games. I guess I could download another and try it.

---

### Post by brk3 on 2005-08-27
Its just Im wondering do you have your 3d set up properly or is just that paticular game. most likely the first one. Have you installed the nvidia drivers?

---

### Post by rdh002 on 2005-08-27
[QUOTE=brk3]Its just Im wondering do you have your 3d set up properly or is just that paticular game. most likely the first one. Have you installed the nvidia drivers?[/QUOTE]
 Yes  glxgears runs about 1850 fps   with mx440  card

---

### Post by brk3 on 2005-08-27
Not really sure so, sorry. Have been googling a bit for you, just try one thing: try running it as root.(sudo /home/dad/.etwolf/etmain)

---

### Post by rdh002 on 2005-08-27
[QUOTE=brk3]Not really sure so, sorry. Have been googling a bit for you, just try one thing: try running it as root.(sudo /home/dad/.etwolf/etmain)[/QUOTE]
 Thanks I will try that . Appriciate the response!

---

