---
title: "[News] Nexuiz 2.0 released"
date: 2006-06-14
forum: Gaming &amp; Leisure
---

### Post by Ctrl+Alt+Del on 2006-06-14
For those of you who haven't played Nexuiz in the past here's a short about taken from their page:
Nexuiz is a 3d deathmatch game project, created online by a team of developers called Alientrap. It is available for download for Windows, Mac, and Linux (all the same archive).The first version was released May 31st 2005, released entirely GPL and free over the net, a first for a project of its kind. Since the release the game is still being updated and developed, currently at version 2.0 and new releases being developed.
Version 2.0 is another massive update to the game, new features such as a single player campaign with completely new advanced bot AI, five new maps, new particle effect system, weapon changes, and complete precompiled bumpmapping with GLSL shaders. We have also optimized the game heavily, and improved net performance.

(incomplete) Changelog:
[http://www.alientrap.org/dude/newfeatures20.txt](http://www.alientrap.org/dude/newfeatures20.txt)
Video:
[http://www.youtube.com/watch?v=4E5kRPp9m3E](http://www.youtube.com/watch?v=4E5kRPp9m3E) or [http://verm.planetnexuiz.com/Nexuiztrailer.avi](http://verm.planetnexuiz.com/Nexuiztrailer.avi)
Forumpost:
[http://www.alientrap.org/forum/viewtopic.php?p=5117#5117](http://www.alientrap.org/forum/viewtopic.php?p=5117#5117)
Some Screenshots from the 1.x version can be found here:
[http://www.alientrap.org/nexuiz/index.php?module=media](http://www.alientrap.org/nexuiz/index.php?module=media)

peaked your interest? head over to [http://www.alientrap.org/nexuiz/index.php?module=downloads](http://www.alientrap.org/nexuiz/index.php?module=downloads) and grab your copy while it's still warm and crispy :)

---

### Post by FredB on 2006-06-14
Great ! I will download it asap. let's hope servers won't be down ;)

Edit : Servers down :(

> Warning: mysql_connect(): Too many connections in /home/alientrap/domains/alientrap.org/public_html/nexuiz/bin/func_main.php on line 3

Warning: mysql_select_db(): supplied argument is not a valid MySQL-Link resource in /home/alientrap/domains/alientrap.org/public_html/nexuiz/bin/func_main.php on line 4

Warning: mysql_query(): Too many connections in /home/alientrap/domains/alientrap.org/public_html/nexuiz/bin/func_main.php on line 27

Warning: mysql_query(): A link to the server could not be established in /home/alientrap/domains/alientrap.org/public_html/nexuiz/bin/func_main.php on line 27
# ack! query failed: errorno=1040
# error=Too many connections
# query=select * from STATS where IP = '82.125.222.14' and RECEIVED = now()

---

### Post by Ctrl+Alt+Del on 2006-06-14
try [http://prdownloads.sourceforge.net/nexuiz/nexuiz-20.zip?download](http://prdownloads.sourceforge.net/nexuiz/nexuiz-20.zip?download) for the download :)

---

### Post by linuksamiko on 2006-06-14
I was looking for a repository for Nexuiz. Is there a Server providing Nexuiz for dapper?

---

### Post by Ctrl+Alt+Del on 2006-06-14
Not to my knowledge, but installation is simple, just unpack the zip file and launch nexuiz-linux-686-sdl

---

### Post by Fallom on 2006-06-14
Nexuiz is a lot of fun, and it reminds me of all the old Quake deathmatches I've played.

When I run it on Dapper, though, I get strange hitches in the gameplay even though my FPS is 100+. It's definitely not lag because it does it even in a bot match.

---

### Post by rjcube on 2006-06-14
So far Nexuiz is my favorite linux game...the only problem is that i cant get the sound to work right, hopefully it works in 2.0.

---

### Post by Onyros on 2006-06-14
We have to set up a server for ubuntu forum dwellers ;)

I just tried it, too, and it looks and feels quite good.

I am, probably, the worst FPS player the world has ever seen, but it's always good fun. And Nexuiz seems to be faster than most FPS' I've ever seen (it's really not my type of game, but this one seems incredibly fast).

---

### Post by jISh on 2006-06-15
If anyone gets a server set up, I'll be sure to pub there often :)

---

### Post by FredB on 2006-06-15
I downloaded it. And it runs great, even if it is a little laggy on my P4 - 2.6 ghz - 1 Gb - GeForce FX 5200 - 128 Mb.

Strange because Doom 3 and Quake 4 are running *smoothly*...

/me goes back to angband ;)

---

### Post by eqisow on 2006-06-15
> I downloaded it. And it runs great, even if it is a little laggy on my P4 - 2.6 ghz - 1 Gb - GeForce FX 5200 - 128 Mb.

Strange because Doom 3 and Quake 4 are running smoothly...

So true, this game seems to waste a lot of resources. I'm running an AMD64 3000+, 2 GB RAM, and a GeForce 6800 and I lag in firefights at 1024 res and default settings. Something has to be done about that before this game can find a permanent home on my HD. :(

---

### Post by FredB on 2006-06-15
Try a lower resolution. Like 800x600. And you'll have a fps boost ;)

->[]

---

### Post by eqisow on 2006-06-15
> Try a lower resolution. Like 800x600. And you'll have a fps boost 

Indeed, 800x600 would give a higher FPS, but I can't stand to run games at 800x600. It looks horrible. Further, my point was that with my system setup I shouldn't *have* to run any current game at that resolution, especially one as graphically unimpressive as Nexuiz.

Besides, it's essentially an older version of Unreal Tournament, so I'll just stick with UT 2004.

---

### Post by FredB on 2006-06-15
Personnaly, I started FPS with Doom, so having a 320x200 resolution. I played Quake -> Quake 3 Arena (included) from 512x384 to 1024x768... So 800x600 is not a bad thing for me at least ;) 

Unimpressive ? I think the engine is kinda CPU hungry, but don't forget, it was quake engine at the beginning... So a very old engine, heavily modified ;)

---

### Post by Ctrl+Alt+Del on 2006-06-15
Nexuiz does not have killergraphics overall, but it has some features that are very well able to choke a high-end machine to death.
Turning off bloom can boost performance drastically.
Apart from that nexuiz has several prebuilt configs tha can be executed from the console.
open the ingame console and type:
exec configname.cfg

available configs are:
low.cfg
med.cfg
normal.cfg
high.cfg
ultra.cfg
ultimate.cfg

---

### Post by eqisow on 2006-06-15
> Nexuiz does not have killergraphics overall, but it has some features that are very well able to choke a high-end machine to death.

Indeed, I actually noticed this. However, even with everything off except decals and realtime world lighting and textures on good it's still not really playable. It might be good enough for a single player campaign (if there was one), but on multiplayer where lag = instant death, it just won't do.

---

### Post by Asraniel on 2006-06-15
i suggest you turn off everything that has to do with realtime ligths, normaly those are the ones that kill your pc..

well, in the new nexuiz version there are a few more options that want to kill your pc, but they look realy good..

---

### Post by Oblong_Cheese on 2006-06-15
There is a single-player campaign in v2.0.

Also, the game runs at ~90fps on my 6800GT with everything on high/full (except with bloom disabled) in 1024x768 (x86-64 version).

---

