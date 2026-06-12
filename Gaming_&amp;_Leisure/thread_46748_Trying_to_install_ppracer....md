---
title: "Trying to install ppracer..."
date: 2005-07-06
forum: Gaming &amp; Leisure
---

### Post by WMCoolmon on 2005-07-06
...I couldn't find the package in apt, so I decided to try compiling.

Most important messages bolded

> checking for location of tclConfig.sh... /usr/lib/tcl8.4/tclConfig.sh
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for SDL_JoystickOpen... no
*** This version of SDL doesn't have joystick support.
*** Configuring without joystick support.
checking for Mix_OpenAudio in -lSDL_mixer... no
***** SDL_mixer not found.  Configuring without audio support.**
checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
*** Hmm, you don't seem to have OpenGL libraries installed in the standard
*** location (/usr/lib).  I'll check in /usr/X11R6/lib, since
*** many distributions (incorrectly) put OpenGL libs there.
checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
**configure: error: Cannot find GL library**

Now, I've got libsdl-mixer installed, and I've also got as many seemingly-relevant OpenGL "-dev" packages installed that I can find. Should I care about the sdl_mixer error, and is there any way to satisfy the OpenGL dependency?

If there's anything else I should do (ie I've heard "checkinstall" will make it easy to uninstall later on), please mention it. :)

---

### Post by Xian on 2005-07-06
This [THREAD](http://ubuntuforums.org/showthread.php?t=13513) has some information.

---

### Post by WMCoolmon on 2005-07-07
Yeah, I already saw that thread and installed both build-essential and libsdl-dev. :-/

---

