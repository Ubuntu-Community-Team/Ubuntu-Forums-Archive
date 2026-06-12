---
title: "Scrolling Bug in Compiz"
date: 2009-01-24
forum: General Help
---

### Post by cdahmedeh on 2009-01-24
Hello,

I noticed that when Compiz Fusion is enabled and when I scroll a window, video playback windows flashes black repeatedly until I stop scrolling.

How to repreduce error (step by step) :
1. Open any Window with long scroll bar (ie. Firefox)
2. Open right next to it a Video playing (like in VLC or Totem)
3. While keeping both windows visible, scroll with Firefox.
4. Notice how the Video Overlay keeps flashing in weird black and checkerboard patterns.

Does anyone know how to fix such problem ?

Specs :
Ubuntu Linux, Intrepid Ibex 8.10
nVidia Driver version 177
8600m GT video card (in Dell XPS m1530 laptop)

---

### Post by binbash on 2009-01-24
which video output are you using at vlc or totem?

---

### Post by cdahmedeh on 2009-01-24
I'm not sure I think either OpenGL or X11 Video Plugin or something like that.

EDIT : Solution found : Setting VLC to OpenGl rather than the default X11 video extension fixed the problem. Is it possible to change the rendering method in Totem ?

---

### Post by binbash on 2009-01-24
I dont know the totem stuff but this bug will be fixed soon.At least ATI side.

---

