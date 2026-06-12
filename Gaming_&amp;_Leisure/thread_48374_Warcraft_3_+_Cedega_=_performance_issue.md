---
title: "Warcraft 3 + Cedega = performance issue"
date: 2005-07-12
forum: Gaming &amp; Leisure
---

### Post by Heliode on 2005-07-12
Hey everyone,

I've installed Cedega (4.3.2) and with it I've installed Warcraft 3. However, it runs very, very slow, even with all the options set to the lowest possible setting it is still unplayable. This is strange, because I'm also using Cedega to run Jedi Knight: Jedi Academy, which runs as fast as it does in Windows. I'm also running UT2004 and Doom 3 natively, and they also run very well.

Some specs:
3 Ghz HT processor
1 GB of ram
Radeon 9800 XT
fglrx driver 8.12.10 running 

I've read all over the place that Warcraft should run just fine, so this is very frustrating... if anyone could be of any help at all it would be greatly appreciated!

---

### Post by frodon on 2005-07-12
same for me, maybe performance are better with cedega 4.3.2.

---

### Post by Gnobody on 2005-07-12
[QUOTE=frodon]same for me, maybe performance are better with cedega 4.3.2.[/QUOTE]
 Sounds like it isn't using hardware rendering.  Enable the dashboard see what kind of framerates you get if it less than 70 fps then GL rendering is probably being done in software.

---

### Post by DarkManX4lf on 2005-07-12
well first of all, D3D (directx) games do not run so well in linux, openGL games on the other hand do ru n well in linux, thats why UT2004, doom3 can run fine, and when you use cedega to run jedi knight its using openGL since Jedi Knight uses the Quake 3 engine and the quake 3 engine uses openGL,

So...what you should try to do is this:


open up your terminal/console
 
go to your warcraft 3 dir  (  cd /path/to/your/war3/dir  ), and type this

cedega war3 -opengl

and it now it s hould be running in openGL, now remember not all games are capable of running in opengl. i also urge you to use the new ati drivers for linux from the ati website, i belive its version 8.14.13, it boosts performance by alot.


this How To: [http://www.ubuntuforums.org/showthread.php?t=32495&highlight=8.14.13](http://www.ubuntuforums.org/showthread.php?t=32495&highlight=8.14.13)

will help you get the 8.14.13 drivers to work

---

### Post by gil-galad on 2005-07-12
Very strange.  It sounds like the 3d isn't working, but if it does work in jedi acadamy, then 3d should be working.

---

### Post by Heliode on 2005-07-13
[QUOTE=DarkManX4lf]

open up your terminal/console
 
go to your warcraft 3 dir  (  cd /path/to/your/war3/dir  ), and type this

cedega war3 -opengl
[/QUOTE]

Wow, that completely fixed it! It runs completely smooth now! Thanks a lot!!

---

### Post by DarkManX4lf on 2005-07-13
no problem :)

---

