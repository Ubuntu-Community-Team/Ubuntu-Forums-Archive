---
title: "Wolfenstein Enemy Territory on Ubuntu 14.04"
date: 2014-07-22
forum: Gaming &amp; Leisure
---

### Post by jballer0602 on 2014-07-22
I was wondering if someone could help me out and make a updated version of an Enemy territory guide.

This is the guide I used

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

The only problem is when it asks me to get permission to copy the updated extracted files to overwrite them over the ones i already have in the directory so the game would be updated.



sudo chown root:root et*.x86
sudo mv et*.x86 /usr/local/games/enemy-territory/

^^^
These Commands will not work when i put them in, this is what I get when they are entered.

root@jerome-K55N:/home/jerome# sudo chown root:root et*.x86
chown: cannot access &#8216;et*.x86&#8217;: No such file or directory
root@jerome-K55N:/home/jerome# sudo mv et*.x86 /usr/local/games/enemy-territory/mv: cannot stat &#8216;et*.x86&#8217;: No such file or directory

It keeps saying that there is no file or directory even though there is.
Will anybody show me the way?

Also it looks like I need to be OWNER of the directory to get the permissions. How would i become owner?

---

### Post by oldrocker99 on 2014-07-22
Are those files in the root of your home folder? In other words, are all the *exe files in the home folder itself, and not in a directory? If they are, you need to cd to that directory before you run the chown and mv commands. Otherwise, you'll get the "no such file or directory" error.

Just a guess...

---

### Post by jballer0602 on 2014-07-22
Ok well after a bunch of trial and error. I'm able to run ET but i get this error

root@jerome-K55N:/home/jerome# et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/root/.etwolf/etmain
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

---

### Post by Peter_Solver on 2014-07-24
Do you have PlayDeb installed on your computer? I hope this helps: [http://www.n00bsonubuntu.net/content/install-wolfenstein-enemy-territory-using-playdeb/](http://www.n00bsonubuntu.net/content/install-wolfenstein-enemy-territory-using-playdeb/)

---

### Post by mastablasta on 2014-07-25
yes, add playdeb repository to software sources then you can just install it from software center.

---

