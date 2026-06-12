---
title: "Alien Arena 7.51 released"
date: 2011-03-12
forum: Gaming &amp; Leisure
---

### Post by Irritant on 2011-03-12
Howdy kiddos - official press release

**A**lien Arena 2011 version 7.51 has been released today!

COR Entertainment has released Alien Arena 2011 for Windows and Linux/Unix.

Some of the new features for this release include: 

[list]
[*]Extensive rewrite of bsp surface rendering for a massive performance increase
[*]Complete rewrite of vertex buffer object code
[*]Complete rewrite of post process effects
[*]Improvements to shadow mapping for dynamic shadows
[*]Variety of graphical updates and bugfixes
[*]Three new/revamped levels
[*]Added downloading of iqm meshes
[/list]
Alien Arena 2011(v7.51)

[[img]http://red.planetarena.org/mediathumbs/normalmap_m.jpg[/img]](http://red.planetarena.org/mediathumbs/normalmap.jpg) [[img]http://red.planetarena.org/mediathumbs/liquid_m.jpg[/img]](http://red.planetarena.org/mediathumbs/liquid.jpg)
[[img]http://red.planetarena.org/mediathumbs/ppixelmartian_s.jpg[/img]](http://red.planetarena.org/mediathumbs/ppixelmartian_m.jpg) [[img]http://red.planetarena.org/mediathumbs/liquid2_m.jpg[/img]](http://red.planetarena.org/mediathumbs/liquid2.jpg)
[[img]http://red.planetarena.org/mediathumbs/violator2_m.jpg[/img]](http://red.planetarena.org/mediathumbs/violator2.jpg) [[img]http://red.planetarena.org/mediathumbs/purg_m.jpg[/img]](http://red.planetarena.org/mediathumbs/purg_big.jpg)

video - [http://www.youtube.com/watch?v=YNvep_oWFbs](http://www.youtube.com/watch?v=YNvep_oWFbs)

For a complete changelog - [http://icculus.org/alienarena/changelogs/7.51.txt](http://icculus.org/alienarena/changelogs/7.51.txt)

For more information, new media, and to download the game visit [http://red.planetarena.org](http://red.planetarena.org)

---

### Post by tommcd on 2011-03-12
Thanks for the news about Alien Arena! 
This tends to be a rather underrated game around here. I have always liked it though. 
The [http://www.phoronix.com/](http://www.phoronix.com/) website tends to keep on top of linux gaming news; but they have nothing about the new Alien Arena as I write this. 
I am downloading the new Alien Arena now!

---

### Post by Perfect Storm on 2011-03-12
Really nice! *downloading*

---

### Post by J.K.Makowka on 2011-03-12
Nice, but since it is mostly about performance increase, could you give us some additional information, just how much it increase? Maybe before and after FPS?
Can't test it my self right now, but I would be interested in how much faster it really is.

---

### Post by Brebs on 2011-03-12
The executable names are still crx and crx-ded :(

These names are meaningless to new users, and just cause confusion. When a new user's freshly installed the game from the command-line, what do you think the user would assume the executable is called ;)

Please rename to alienarena and alienarena-ded.

---

### Post by Irritant on 2011-03-12
> **J.K.Makowka said:**
> Nice, but since it is mostly about performance increase, could you give us some additional information, just how much it increase? Maybe before and after FPS?
Can't test it my self right now, but I would be interested in how much faster it really is.

The increase is around 40-50% from version 7.50, depending of course on system factors, but that seemed to be the average from our testing over a pretty wide variety of systems.  Most of this was accomplished in the map rendering routines.  In a previous release we had sped up the mesh rendering dramatically as well.

---

### Post by Irritant on 2011-03-12
> **Brebs said:**
> The executable names are still crx and crx-ded :(

These names are meaningless to new users, and just cause confusion. When a new user's freshly installed the game from the command-line, what do you think the user would assume the executable is called ;)

Please rename to alienarena and alienarena-ded.

That is a good point, we will do that with our next release.

---

### Post by 23Andrew on 2011-03-12
*downloads*
EDIT:
When I run ./configure I get:

...
checking whether pthreads work without any flags... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for library containing jpeg_read_header... no
configure: error: "Required jpeg library not found."

What should I do?

---

### Post by Irritant on 2011-03-12
> **23Andrew said:**
> *downloads*
EDIT:
When I run ./configure I get:

...
checking whether pthreads work without any flags... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for library containing jpeg_read_header... no
configure: error: "Required jpeg library not found."

What should I do?

You need to install libjpeg.  Here is a good thread that should help with any missing dependencies - [http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4422&page=2](http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4422&page=2)

---

