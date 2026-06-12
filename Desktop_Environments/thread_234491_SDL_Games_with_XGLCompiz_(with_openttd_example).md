---
title: "SDL Games with XGL/Compiz (with openttd example)"
date: 2006-08-11
forum: Desktop Environments
---

### Post by uzusan on 2006-08-11
Just thought i would pass on a tip that i came across while trying to get OpenTTD to work with ubuntu while using XGL/Compiz.

the problem with running sdl games while using xgl/compix is that the window becomes transparent and the game is unplayable.

I came across [this guide]("http://linux.net.pl/~harnir/2006-04-22/how-to-run-sdl-and-opengl-based-games-under-xgl/")

run this from a command line.
XLIB_SKIP_ARGB_VISUALS=1 ./openttd

It also has a guide on running opengl games but ive not tried that yet.

---

