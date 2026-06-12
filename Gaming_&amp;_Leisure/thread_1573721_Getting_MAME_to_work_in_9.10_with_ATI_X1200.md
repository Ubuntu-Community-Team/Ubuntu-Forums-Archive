---
title: "Getting MAME to work in 9.10 with ATI X1200?"
date: 2010-09-13
forum: Gaming &amp; Leisure
---

### Post by HangukMiguk on 2010-09-13
I am running 9.10 in 64-bit and am trying to run MAME emulators.  Most specifically, I'm trying to use Final Burn Alpha in WINE, but other, Linux, MAME emulators have the same problems.

Even on much older games (Ex. Street Fighter II Hyper Fighting, Super Street Fighter II), I have major framerate issues where the game slows down to a virtual crawl.  I have used every possible graphical support to no avail.

I'm assuming it may be a problem with my video card.  I know this emulator worked in Vista for me, but I also realize that ATI stopped officially supporting this video card series.

Is this actually a problem with my video card, and is there something I can do to update the drivers to make this work?  Or am I SOL?

EDIT:  I ran the emu through term, and here's a couple of errors:

```
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:d3d_surface:IWineD3DBaseSurfaceImpl_Blt Can't handle WINEDDBLT_ASYNC flag right now.
```

Maybe it's an OpenGL problem.  I'll try something and see if it fixes it.

```
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 (RS690 791F) 20090101  NO-TCL
```

EDIT: I got told that Catalyst 9.3 SHOULD work in 9.10...trying to install, but got the following error message:

```
Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.31-17-generic; make sure that the version is being
correctly set by --iscurrentdistro
```

---

