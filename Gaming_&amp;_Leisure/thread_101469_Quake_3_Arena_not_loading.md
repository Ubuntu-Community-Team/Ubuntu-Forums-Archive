---
title: "Quake 3 Arena not loading"
date: 2005-12-09
forum: Gaming &amp; Leisure
---

### Post by Kobra on 2005-12-09
Ok, I got it installed, Point Release installed, and the pak0.pk3 file transfered.  But when I try loading it, it gives me this error ```
534 files in pk3 files
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Couldn't load default.cfg

```
Whats up with this?

---

### Post by bjweeks on 2005-12-09
You don't have all the .pk3 files or there not in the right place.

---

### Post by Kobra on 2005-12-09
I have pak0.pk3 up to pak8.pk3, and their all in the baseq3 file.  This is the same problem that kept me from playing back on Gentoo

---

### Post by Kobra on 2005-12-09
Nevermind.   We found the problem.  I installed Quake 3 in /usr/games, and it's looking for /usr/local/games

---

### Post by Moucxs on 2006-01-07
hello , 

ime getting the same error,
(default.cfg missing)
when i took a look in the baseq i have  8 folders (1 till 8 no pak0 file)

any tips ? i already tryd googeling, (and still am)

when i find it before its posted i will post the sollution 

greetz

---

### Post by El Rey de Todo on 2006-04-13
Did you ever figure ut the solution to the default.cfg problem?  I'm having that issue now and have no idea how to fix it!

---

### Post by crane on 2006-04-14
I remember having this issue when I firstinstalled the game. I can't quite remember what the issue was. You may need to make a default.cfg file in your ~/.q3base directory or it could be a permissions issue. Can you run the game as root? (sudo quake3)

---

### Post by fng on 2006-04-14
[QUOTE=Moucxs]ime getting the same error,
(default.cfg missing)
when i took a look in the baseq i have  8 folders (1 till 8 no pak0 file)[/QUOTE]

You really need the pak0.pk3. It's like a big zip file containing all needed files, like default.cfg.
Quake 3 won't play without this file. You can find the file on the installation cd.

---

