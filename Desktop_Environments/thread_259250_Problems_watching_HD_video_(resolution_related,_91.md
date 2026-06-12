---
title: "Problems watching HD video (resolution related, 915resolution?)"
date: 2006-09-17
forum: Desktop Environments
---

### Post by &#12465;&#12452;&#12488; on 2006-09-17
When attempting to watch high definition video on my laptop, every application fails on launch. I tried to check the debug (for mplayer), and it goes like this:

Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 


This does seem quite obviously to have something to do with my resolution. However, I am actually running at 1280x800, so this thing shouldn't be too huge, no. But come to think of it, I've had more problem with resolutions in some programs attempting to do full s creen. If some application is running a resolution that's not 1024x768 or 1280x800, it doesn't seem to work, if I recall correctly.

The laptop's video acceleration is an i810. Could this be a bug/limitation of 915resolution?

---

### Post by jshayden on 2007-01-10
^bump

I have the same exact problem.

---

### Post by easy2love on 2007-02-25
I also met the same problem.

---

### Post by fajoes on 2007-06-01
I've got the same problem.
I just found this [http://blog.sontek.net/archive/2007/04/04/Error-BadAlloc-insufficient-resources-for-operation.aspx](http://blog.sontek.net/archive/2007/04/04/Error-BadAlloc-insufficient-resources-for-operation.aspx)

but I haven't test yet

---

### Post by fajoes on 2007-06-01
it work's :D
just tested with starcraft 2 1280x720 demo movie

---

