---
title: "Planet Penguin Racing"
date: 2005-08-31
forum: Gaming &amp; Leisure
---

### Post by ConnorP on 2005-08-31
i dont know how to install!

its as simple as that!

im very new to everything Ubuntu and dont even know what most of the installation inscructions mean...

a step by step walkthrough i would truly appreciate!  :)

im only used to installing things through apt-get...

---

### Post by Hobbsee on 2005-09-01
[QUOTE=ConnorP]i dont know how to install!

its as simple as that!

im very new to everything Ubuntu and dont even know what most of the installation inscructions mean...

a step by step walkthrough i would truly appreciate!  :)

im only used to installing things through apt-get...[/QUOTE]
 or better still, could we get it in the repositries?  even the backports?

---

### Post by Lord Illidan on 2005-09-01
I take it you downloaded the .tar.bz2 file from here, right : [http://projects.planetpenguin.de/racer/downloads.php](http://projects.planetpenguin.de/racer/downloads.php)

So then all you have to do is rightclick on the folder, and tell it to Extract Here.

Then, open a terminal, and cd to the folder...

Then once you have opened the folder, enter this command

```
./configure
``` 

A bunch of text will start scrolling down the screen. Give us the output, copy and paste, then we'll tell you what to do next.

EDIT : Actually I tried it, and it is no better than TuxRacer...

---

### Post by ConnorP on 2005-09-01
ok, this is what i get with ./configure

root@ubuntu:/home/connor # cd ppracer-0.3.1
root@ubuntu:/home/connor/ppracer-0.3.1 # ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

---

### Post by void_false on 2005-09-01
"apt-get install build-essential" then try again.

---

### Post by ConnorP on 2005-09-01
[QUOTE=void_false]"apt-get install build-essential" then try again.[/QUOTE]
 that worked, but then i got this
[B]
checking for location of tclConfig.sh... configure: error: tclConfig.sh not found - use the --with-tcl option[/B]

---

### Post by GTvulse on 2005-09-01
[QUOTE=ConnorP]that worked, but then i got this
[B]
checking for location of tclConfig.sh... configure: error: tclConfig.sh not found - use the --with-tcl option[/B][/QUOTE]
 You have to install all the development packages required by the dependencies. What I do is to open a second terminal and there, first use apt-cache search to find, e.g., "tcl-dev" and then apt-get the needed packages. Of course, you can use Synaptic's search facility as well. In general it is a business of trying till you have installed all the dependencies (that is, the configuration script doesn't fail anymore).

---

### Post by nickless on 2005-09-01
[QUOTE=Lord Illidan]
EDIT : Actually I tried it, and it is no better than TuxRacer...[/QUOTE]
Thought there would be a multiplayer option?

---

### Post by ConnorP on 2005-09-01
i did that and i was able to get it up to here befor e i got totally confused

[B]checking for SDL - version >= 1.2.0... yes
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
configure: error: Cannot find GL library[/B]

---

### Post by void_false on 2005-09-01
Follow dradul's suggestion.

---

### Post by ConnorP on 2005-09-01
ok i did..but now im totally helpless because when i do "make" i get this un-understandable message...

[B]tcl_util.cpp:37: error: invalid conversion from `const char*' to `char*'
tcl_util.cpp: In function `int get_tcl_int_tuple(Tcl_Interp*, const char*,
   int*, int)':
tcl_util.cpp:76: error: invalid conversion from `const char*' to `char*'
make[2]: *** [tcl_util.o] Error 1
make[2]: Leaving directory `/home/connor/ppracer-0.3.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/connor/ppracer-0.3.1'
make: *** [all] Error 2[/B]

---

### Post by moonballoon on 2006-09-23
I got the same message on Kubuntu 6.06 and it turned out to be a problem with the tcl version.  I solved it by searching for "tcl" in the package manager (aptitude, but the same thing should work with adept), removing every match that was version 8.3 or older, and installing every match that was version 8.4.  I don't know whether tcl 8.4 is available for Hoary, but apparently that is what it takes to get Planet Penguin Racer 3.1 working.

---

