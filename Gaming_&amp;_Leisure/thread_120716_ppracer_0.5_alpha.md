---
title: "ppracer 0.5 alpha"
date: 2006-01-23
forum: Gaming &amp; Leisure
---

### Post by edistar on 2006-01-23
Hello!
I wanted to try out the new ppracer alpha as it hast multiplayer mode etc. and it might be a lot of fun playing.
But when I run ./configure it just says:
> configure: error: Cannot find GL library
What can I do? I have installed graphics drivers.....(nvidia)
I hope you can help!
Regards,
Edwin

---

### Post by Perfect Storm on 2006-01-23
Try with:

```
sudo apt-get install libgl1-mesa libgl1-mesa-dev
```

---

### Post by edistar on 2006-01-24
I did that and it still doesn't work.... what can I do to get it work?
Regards,
edwin

---

### Post by Perfect Storm on 2006-01-24
Can you please post the whole output. There may be some informations on it which might prove useful.

---

### Post by edistar on 2006-01-25
Of course, I should have done that at the beginning.......

> checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for getcwd... yes
checking for gettimeofday... yes
checking for strdup... yes
checking for finite... yes
checking for isnan... yes
checking for _finite... no
checking for _isnan... no
checking ieeefp.h usability... no
checking ieeefp.h presence... no
checking for ieeefp.h... no
checking for Win32 platform... no
checking for X... libraries /usr/X11R6/lib, headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for main in -ldl... yes
checking for main in -lm... yes
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for SDL_JoystickOpen... no
*** This version of SDL doesn't have joystick support.
*** Configuring without joystick support.
checking for Mix_OpenAudio in -lSDL_mixer... no
*** SDL_mixer not found.  Configuring without audio support.
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
configure: error: Cannot find GL library

Hope this helps...

---

### Post by Perfect Storm on 2006-01-25
First
> 
checking for Mix_OpenAudio in -lSDL_mixer... no
*** SDL_mixer not found. Configuring without audio support.

You might want sound so I'll suggest you install SDL_mixer and SDL_mixer-dev

```

sudo apt-get install SDL_mixer SDL_mixer-dev

```


I see you're on a 64bit ubuntu/linux that might be the problem. I have no experience with 64 bit. But you might want to install linux32 file if you havn't and what I've heard you need to make symblinks into linux32 folder.
It's better if a 64 bit users can explain it more correctly, because I've absolutly no experience with 64 bit.

---

### Post by simplyw00x on 2006-01-25
For some reason it's not finding GL, MesaGL or SDL Mixer. Make sure all are installed and then try passing options to configure to manually tell them where you installed those libs.

---

### Post by edistar on 2006-01-25
Thanks for helping,
> Make sure all are installed and then try passing options to configure to manually tell them where you installed those libs.
How do I do that?
Btw.: when I did sudo apt-get install SDL_mixer SDL_mixer-dev it said that it could not find SDL_mixer...

Regards,
Edistar

---

### Post by Perfect Storm on 2006-01-25
sorry it should be

```
sudo apt-get install libsdl-mixer1.2 libsdl-mixer1.2-dev
```

Happens when doing 10 things at the same time :P

---

### Post by edistar on 2006-01-27
> 	For some reason it's not finding GL, MesaGL or SDL Mixer. Make sure all are installed and then try passing options to configure to manually tell them where you installed those libs.
How do I do that? Thanks for helping...
Regards,
Edistar

---

### Post by Jpenguin on 2006-01-28
I am on ppc & I am have ing the same exact problem.  It cant find GL or SDL whend I'vee installed them.  I also trying to compile PINGUS svn, but it says I don't have CLANLIB but i do!

---

### Post by Jpenguin on 2006-01-28
compile everything from source,

---

### Post by edistar on 2006-02-01
what do I have to compile?! I'm sorry, still learning Ubuntu and GNU/Linux in general...
Regards,
Edistar

---

