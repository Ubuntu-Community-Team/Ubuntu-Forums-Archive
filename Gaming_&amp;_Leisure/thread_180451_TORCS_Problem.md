---
title: "TORCS Problem"
date: 2006-05-22
forum: Gaming &amp; Leisure
---

### Post by Klaidas on 2006-05-22
Hello :)
I'm pretty new to gaming on Ubuntu.
To try out, I installed TORCS. But... I can't run it!
[QUOTE=Klaidas's terminal]klaidas@ubuntu:~$ torcs
Visual Properties Report
------------------------
Compatibility mode, properties unknown.
WARNING: ssgLoadTexture: Cannot determine file type for './(null)'
torcs-bin: indirect_vertex_array.c:1359: __indirect_glTexCoordPointer: Assertion `a != ((void *)0)' failed.
/usr/games/torcs: line 52: 15851 Aborted                 $LIBDIR/torcs-bin -l $LOCAL_CONF -L $LIBDIR -D $DATADIR $*
klaidas@ubuntu:~$
[/QUOTE]

What is the problem? :-|

---

### Post by gard on 2006-07-12
Hi,

I am running in to the same problem.  I started TORCS, configured a player with one of the default cars, selected new race, made sure my player had the focus, and tried both new race and practice.  Both times, I can see it loading the players and cars etc., and then the Torcs screen goes away.  If I run it from a terminal, I see the following:

[FONT="Courier New"]
[COLOR="DarkGreen"]Visual Properties Report
------------------------
Compatibility mode, properties unknown.
freeglut (/usr/lib/torcs/torcs-bin): Unable to create direct context rendering for window '/usr/lib/torcs/torcs-bin'
This may hurt performance.
WARNING: ssgLoadTexture: Cannot determine file type for './(null)'
OpenAL backend info:
  Vendor: OpenAL Community
  Renderer: Software
  Version: 1.1
  Available sources: 1024 or more
  Available buffers: 1024 or more
  Dynamic Sources: requested: 1003, created: 1003
  #static sources: 21
  #dyn sources   : 1003
torcs-bin: indirect_vertex_array.c:1359: __indirect_glTexCoordPointer: Assertion `a != ((void *)0)' failed.
/usr/games/torcs: line 52: 16010 Aborted                 $LIBDIR/torcs-bin -l $LOCAL_CONF -L $LIBDIR -D $DATADIR $*[/FONT][/COLOR]


I am running Ubuntu 6.0.6.  Thanks for any assistance,
gard

---

### Post by meixiang on 2006-10-08
I had the same problem with 6.0.6 too, a new version of Mesalib fixed it. The default MesaLib with 6.0.6 should be 6.4.1. I downloaded version 6.4.2, compiled it, copy the libGL.so.1.5.060402 to /usr/lib. relink the symbol link /usr/lib/libGL.so.1 to libGL.so.1.5.060402. When run torcs again, it does not abort. Hope this help!

---

