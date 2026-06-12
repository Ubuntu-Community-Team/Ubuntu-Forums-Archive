---
title: "Quake 1 Shareware"
date: 2006-01-26
forum: Gaming &amp; Leisure
---

### Post by Earlie Cuyler on 2006-01-26
*What do I have to do to be able to play Quake 1 under Ubuntu?*

---

### Post by minisori on 2006-01-27
Install any of this clients and copy your pak files in there.

[http://www.fuhquake.net/](http://www.fuhquake.net/)
[http://www.quakeforge.net/](http://www.quakeforge.net/)
[http://icculus.org/twilight/darkplaces/](http://icculus.org/twilight/darkplaces/)

---

### Post by Zodiac on 2006-01-27
Is that fuhquake a stand alone game? Or would I need the original Quake 1 CD?

Cause I don't got dat...

---

### Post by Earlie Cuyler on 2006-01-28
[QUOTE=minisori]Install any of this clients and copy your pak files in there.

[http://www.fuhquake.net/](http://www.fuhquake.net/)
[http://www.quakeforge.net/](http://www.quakeforge.net/)
[http://icculus.org/twilight/darkplaces/](http://icculus.org/twilight/darkplaces/)[/QUOTE]

*How do I get the .pak files?*

---

### Post by minisori on 2006-01-28
None of those are stand alone games, because quake is copyrighted. But if u have the old quake or even shareware u only need to copy the id direcotry i think was (the one wich has the.pak files). If u dont have it hmm there was a couple of guys who made a litle quake pak to play multiplayer, if i remember good, one was quake2000.

---

### Post by Satyr451 on 2006-02-09
Hi.  I'm a newb to Ubuntu and I'm also trying to get good old Quake 1 running.  I did an apt-get for something from quakeforge, and that got me closer than previous attempts however, it still doesn't work.  I have the pak.0 and pak.1 files from the full windows version.  

The quake window pops up for a second then closes.  Currently when I try to play, it fails out with a segmentation fault.  

I've installed ubuntu on an old clunker of a laptop just to check it out.  Specs are:

P3 600.
384 Ram
ATI Rage Mobility M3 AGP 2x. 

Below is the terminal output when I try to launch:

IN_LL_Shutdown
VID_Shutdown
Segmentation fault
thomas@test:/usr/games$ qw-client-glx
Added packfile /usr/share/games/quake/id1/pak0.pak (339 files)
IP address 127.0.0.1:27001
UDP (IPv4) Initialized
16.0 megabyte heap.
VID: VidMode version: 2.2
GL_VERSION: 1.2 (1.5 Mesa 6.2.1)
GL_VENDOR: Mesa project: [www.mesa3d.org](www.mesa3d.org)
GL_RENDERER: Mesa GLX Indirect
GL_EXTENSIONS: 
-----------data omitted for brevity----------------
Video mode 640x480 initialized.
Particles: Vertex Array use disabled.
Sprites: 4 maximum vertex elements.
Text: Vertex Array use disabled.
Could not load plugin "/usr/lib/quakeforge/plugins/snd_output_default.so".
Loading of sound output module: default failed!
CDAudio_Init: No CD in player.
CD Audio Initialized
VID: DGA version: 2.0
JOY: Joystick not found.
Received signal 11, exiting...
IN_Shutdown
IN_LL_Shutdown
VID_Shutdown
Segmentation fault


Any help out there?

---

