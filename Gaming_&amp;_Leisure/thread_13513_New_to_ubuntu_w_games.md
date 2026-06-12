---
title: "New to ubuntu /w games"
date: 2005-02-01
forum: Gaming &amp; Leisure
---

### Post by Wuzzbent on 2005-02-01
Hey all,
  I just bought linux format mag for the ubuntu distro disks,  I have it all installed and running quite nicely, but my experience with linux is limited and I seem to have problems running games.. the 1 of 2 disks that came with the mag has a few games I would like to run but I can't get them started for the life of me.  every game that I ./configure throws a bunch of errors and bails on me.  I get a plethora of errors stating I don't have certain lib's installed, or the script cannot find this file or that file.  but when I look in the package viewer,  the packages are installed so I'm a bit confused.  This install is a normal ubuntu install and I haven't added anything, can someone point me in the right direction on what I need to do to set my sytsem up to play games?

Thanks..

Wuzzbent

---

### Post by Dylanby on 2005-02-01
Perhaps if you list the specific games you want to get up & running people could offer specific solutions for each game.

---

### Post by Wuzzbent on 2005-02-01
[QUOTE=Dylanby]Perhaps if you list the specific games you want to get up & running people could offer specific solutions for each game.[/QUOTE]


Ok I'm trying to install Scourge, which came on one of the distro cd's,  I have installed everyting that I know to install, i have installed all the mesa packages, all the SDL packages, im at a loss, here is what's happening...

loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for ranlib... ranlib
checking whether make sets ${MAKE}... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/time.h... yes
checking for unistd.h... yes
checking for working const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for getcwd... yes
checking for gettimeofday... yes
checking for strdup... yes
checking for finite... yes
checking for isnan... yes
checking for _finite... no
checking for _isnan... no
checking for ieeefp.h... no
checking for Win32 platform... no
checking for Mac OSX platform... no
checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... no
checking for main in -ldl... yes
checking for main in -lm... yes
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


I'm at a loss,  I don't know where else to look..  My buddy can compile it on his *nix box and he has sent me the link list and I have every lib in the same place he has that the configure uses.    I'm not sure if my enviroment isn't set up correctly or what's going on...

Wuzzbent

---

### Post by Ste on 2005-02-01
Make sure you have the dev packages of the libs aswell.

For example libgtk you would also need libgtk-dev

---

### Post by Buffalo Soldier on 2005-02-01
And don't forget:```
sudo apt-get install build-essential
```

---

### Post by DJ_Max on 2005-02-01
It says you need the GL Libraries, OpenGL, etc which is used with your video card.

---

### Post by dhonn on 2005-02-02
You are defnitely missing updated SDL development packages

run in terminal as root:
**apt-get install libsdl1.2-dev**

---

### Post by francisco_athens on 2006-10-18
> **Wuzzbent said:**
> 

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
Wuzzbent

I had the same problem until I installed xorg-dev in Edgy...
```
sudo apt-get install xorg-dev
```
I didn't seem to need it in Dapper but I have x-dev installed there..
```
sudo apt-get install x-dev
```

heres my complete apt-get line:
```
sudo apt-get install libfreetype6-dev libgl1-mesa-dev libglu1-mesa-dev libsdl1.2-dev libsdl-mixer1.2-dev libxmu-dev subversion autoconf automake xorg-dev libwxgtk2.6-dev
```

---

