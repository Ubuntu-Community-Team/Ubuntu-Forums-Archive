---
title: "3d issue"
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

### Post by arnieboy on 2005-08-28
try this:
go to the profiles directory in your home folder.
```
cd $HOME/.etwolf/etmain/profiles
```
then do a 
```
rm -rf *
```
now start a new game.

---

