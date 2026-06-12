---
title: "Problem compiling scourge (and other GL stuff)"
date: 2005-07-25
forum: Gaming &amp; Leisure
---

### Post by Olrich on 2005-07-25
I recently downloaded [Scourge](http://scourge.sourceforge.net) and ran ./configure.  It seems to go fine until this section.

checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.0.1... yes
checking for SDL_JoystickOpen... no
*** This version of SDL doesn't have joystick support.
*** Configuring without joystick support.
checking for Mix_OpenAudio in -lSDL_mixer... no
*** SDL_mixer not found.  Configuring without audio support.
checking for SDLNet_Init in -lSDL_net... no
*** SDL_net not found.  Configuring without network support.
checking for GL library... no
checking for GL library (with pthreads)... no
checking for MesaGL library... no
checking for MesaGL library (with pthreads)... no
checking for opengl32 library... no
checking for opengl32 library (with pthreads)... no
configure: error: Cannot find GL library

Upon looking at other threads with this problem it was recommended to install build-essential and the -dev versions of all necessary libraries.  I have done all this and my problems still exist.  THe SDL and OpenGL header and library files are in the default locations configure looks in, and even if specify the folder in which they are in, it still fails.  I am running an ATI Radeon 9600 XT on an nForce2 mb, with fglrx working properly.  I am completely at a loss to why this is not working.  Any and all help will be greatly appreciated.

---

### Post by charlieg on 2005-07-25
Have you tried the Scourge Autopackage? Or are you looking to actually develop for Scourge?

If you just want to play it, grab and run the '.package' version of Scourge, which should install automatically:
[http://sourceforge.net/project/showfiles.php?group_id=98006](http://sourceforge.net/project/showfiles.php?group_id=98006)

---

### Post by charlieg on 2005-07-25
Since the 'unable to compile' bit was bothering me, one other thing; do you have mesag-dev and libsdl1.2-dev installed?  They should allow you to compile Scourge (and other GL apps) just fine.

Basically if it's complaining about being unable to find something related to a package when you are tring to compile an application, check for a -dev version of problem package.

---

### Post by Olrich on 2005-07-25
Thanks for the reply, I will download the autopackage, but this is still a problem I would like to fix.  I am 100% sure I have all the -dev versions of the SDL packages, I have even compiled many homebrew applications successfully.

I did not however have mesag-dev. But, if I go to install it in Synaptic it tells me it is going to uninstall tons of stuff like ubunutu-desktop, x-window-core,  and all the xlibmesa packages.   Is this really what I want to do?

I am also curious what the difference between the xlibmesa group of packages is compared to the mesag-dev and assorted packages.  Thanks again and I look forward to anyone's reply.

---

### Post by charlieg on 2005-07-25
Sorry, mesag-dev isn't the one you want but xlibmesa-gl-dev (and probably xlibmesa-glu-dev) instead.

---

### Post by Olrich on 2005-07-25
Hmm..unfortunately I already have those libraries installed.   ](*,) 

I've manually searched the system and found GL/SDL header/library files, and they are all in the correct locations.  

What could be causing configure unable to find these files.  Thanks again for the help.

EDIT:  Well, I got it working, but I'm not entirely sure why.  To compile a test OpenGL program lib Xmu-dev was in the makefile so I downloaded it.  Turns out this lib makes all the SDL and OpenGL stuff work or something.  Thanks for the help.

---

### Post by danabraz on 2005-12-17
I got the same problem on a debian-sid.
After installing libxmu-dev, the .configure worked fine

Thanks a lot[-o<

Yop!
DanY

---

