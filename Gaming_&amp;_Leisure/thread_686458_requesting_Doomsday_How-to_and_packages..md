---
title: "requesting Doomsday How-to and packages."
date: 2008-02-03
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2008-02-03
A new Doomsday release is out : [http://www.happypenguin.org/show?Doomsday%20Engine](http://www.happypenguin.org/show?Doomsday%20Engine)

The problems are :
1. it's a 1.9.0-b5.1 release , meaning still beta
2. It needs to be compiled first.
3. it needs many other packages and files.

I want to request an current (2008) how-to, step by step and if possible make a .deb package from all of it or at least from the source.

I remember  2 years ago i played it on Windows, it was easy to install with only .exe file , now in GNU/Linux it is much more complicated.
 
Thanks.

---

### Post by Perfect Storm on 2008-02-03
```
sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install build-essential cmake checkinstall
sudo aptitude install libxext-dev doxygen lib32ncurses5-dev libgl1-mesa-dev libglu1-mesa-dev libsdl1.2-dev libsdl-net1.2-dev libsdl-mixer1.2-dev libalut-dev zip unzip



cd ~/Desktop
tar zxfv deng-1.9.0-beta5.2.tar.gz
cd deng-1.9.0-beta5.2/deng-1.9.0-beta5.2/build
cmake ../
make
sudo checkinstall
```


Then;

> REQUIREMENTS
------------

In addition to the libraries needed to build Doomsday, you will need
one or more IWAD files from a supported game.  For example, DOOM.WAD
from Ultimate Doom would be suitable.  If you don't own any of the
original games (Doom, Heretic or Hexen), you can always use the
shareware/demo versions.

You won't be able to play without an IWAD file!


ADDITIONAL RESOURCE PACKS
-------------------------

There is a wealth of additional resource packs for Doomsday on the
internet.  One starting point is Doomsday HQ
([http://www.doomsdayhq.com/](http://www.doomsdayhq.com/)).  I recommend also visiting the DHQ
Forums for the latest community buzz.

The must-have packs are the 3D models and detail textures.  You might
also wish to download a music pack (e.g., [http://www.sycraft.org/](http://www.sycraft.org/)).

If you prefer to launch the game from the command line or using a
custom shell script, there are two ways you can load PK3s and WADs:

	1) Use the special automatic resource directories.  You have
	   two options: the user-specific Auto directory, or the
	   system-wide Auto directory.

	   The user-specific Auto directory is located in the runtime
	   directory.  The -userdir option defines the runtime
	   directory.  By default the current directory is used.

	   Let's say you have installed Doomsday into the directory
	   PREFIX.  You will find the subdirectory "share/deng/Data/"
	   under PREFIX.  If you have a resource pack for jDoom,
	   placing it into the system-wide Auto directory
	   "PREFIX/share/deng/Data/jDoom/Auto/" will cause it to be
	   automatically loaded when any user starts jDoom.

	   Note the capital "A" in Auto.

	2) Use the "-file" command line option when you start
	   Doomsday.  If you e.g. have the resource pack
	   ~/mydir/model.pk3, just use "-file ~/mydir/model.pk3".


MIDI MUSIC
----------

Doomsday can play MIDI music using a program of your choosing.  The
environment variable DENG_MIDI_CMD determines the command that will be
used when starting playback of a MIDI music file.

I recommend using MIDI only with sound cards that have hardware
support for playing MIDI music (e.g. SB Live).  Otherwise, it is
advisable to just disable music playback with the "-nomusic" option.

For example, the DENG_MIDI_CMD environment variable could be set like
this:

  export DENG_MIDI_CMD="aplaymidi -p 65:0"

The default program for MIDI playback is "timidity".  Note, however,
that music playback may become choppy since timidity plays music
entirely in software.  It is best to experiment with different
timidity settings (e.g., buffering and process niceness) if you would
like to reduce any artifacts in software music playback.


GLBSP
-----

Beginning with version 1.8.1, Doomsday can generate glBSP data
automatically.  It is no longer necessary to run glBSP separately on
your WADs.

However, if you need it, you can get glBSP from glbsp.sourceforge.net.


RUNNING THE GAME
----------------

These instructions apply to the Linux version of Doomsday.

The Snowberry launcher is available for Linux.

If you prefer launching from the command line, I recommend creating
your own startup scripts for jDoom, jHeretic and jHexen.  In them, you
can specify any command line options you wish to use.  Below is a
simple example.

  #!/bin/sh
  /usr/local/bin/doomsday -game jdoom -file ~/wads/doom.wad \
      -userdir ~/doomsday/jdoom

Before running this script you will need to create the runtime
directory ~/doomsday/jdoom.  All savegame files, message logs and
other such files will be stored in this directory.

The default location for the doomsday executable is /usr/local/bin,
but that can be changed by providing your own prefix for the configure
script (see Build/COMPILING).


---

### Post by MaximB on 2008-02-03
Thanks for the How-to
But I got a problem with "make" :

```
maxim@maxim-ubuntu:~/maxddark/games/deng-1.9.0-beta5.2/deng-1.9.0-beta5.2/build$ cmake ../
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Looking for IceConnectionNumber in ICE
-- Looking for IceConnectionNumber in ICE - found
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Looking for doxygen...
-- Looking for doxygen... - found /usr/bin/doxygen
-- Looking for dot tool...
-- Looking for dot tool... - NOT found
-- Looking for dlfcn.h
-- Looking for dlfcn.h - found
-- Looking for dlopen in dl
-- Looking for dlopen in dl - found
-- ** Graphviz not found. On Ubuntu install graphviz. On Mac OSX install FIXME. On Windows install FIXME.
-- BUILDSCRIPTSDATE:             $LastChangedDate: 2007-01-22 06:50:07 +1100 (Mon, 22 Jan 2007) $
-- CMAKE_SYSTEM:                 Linux-2.6.22-14-generic
-- CMAKE_SYSTEM_PROCESSOR:       unknown
-- CMAKE_BUILD_TYPE:             
-- CMAKE_C_FLAGS:                 
-- CMAKE_C_COMPILER:             /usr/bin/gcc
-- CMAKE_SOURCE_DIR:             /home/maxim/maxddark/games/deng-1.9.0-beta5.2/deng-1.9.0-beta5.2
-- CMAKE_BINARY_DIR:             /home/maxim/maxddark/games/deng-1.9.0-beta5.2/deng-1.9.0-beta5.2/build
-- BUILDJDOOM:                   ON
-- BUILDJHERETIC:                ON
-- BUILDJHEXEN:                  ON
-- BUILDWOLFTC:                  OFF
-- BUILDDOOM64TC:                OFF
-- BUILDJSTRIFE:                 OFF
-- BUILDOPENGL:                  ON
-- BUILDOPENAL:                  OFF
-- BUILDSDLMIXER:                ON
-- BUILDDEDICATED:               OFF
-- BUILDDOX:                     OFF
-- BUILDFIXEDASM:                OFF
-- BUILDSYSTEM:                  UNIX
-- CMAKE_INSTALL_PREFIX          /usr/local
-- DENG_BASE_DIR                 /usr/local/share/deng
-- DENG_LIBRARY_DIR              /usr/local/lib
-- DENG_BINARY_DIR               /usr/local/bin
-- DENG_ENGINE_DATA_DIR          /usr/local/share/deng/data
-- DENG_JDOOM_DATA_DIR           /usr/local/share/deng/data/jdoom
-- DENG_JHERETIC_DATA_DIR        /usr/local/share/deng/data/jheretic
-- DENG_JHEXEN_DATA_DIR          /usr/local/share/deng/data/jhexen
-- DENG_JSTRIFE_DATA_DIR         /usr/local/share/deng/data/jstrife
-- DENG_WOLFTC_DATA_DIR          /usr/local/share/deng/data/wolftc
-- DENG_DOOM64TC_DATA_DIR        /usr/local/share/deng/data/doom64tc
CMake Error: This project requires some variables to be set,
and cmake can not find them.
Please set the following variables:
CURSES_INCLUDE_PATH (ADVANCED)
CURSES_LIBRARY (ADVANCED)

-- Configuring done
maxim@maxim-ubuntu:~/maxddark/games/deng-1.9.0-beta5.2/deng-1.9.0-beta5.2/build$ make
make: *** No targets specified and no makefile found.  Stop.
maxim@maxim-ubuntu:~/maxddark/games/deng-1.9.0-beta5.2/deng-1.9.0-beta5.2/build$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@maxim-ubuntu ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ build ]
3 -  Version: [ 20080203 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ build ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 0
Enter the maintainer's name and e-mail address: 
>> maxim

This package will be built according to these values: 

0 -  Maintainer: [ maxim ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ build ]
3 -  Version: [ 20080203 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ build ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```

And were should I put the WAD siles and the textures and models ?

---

### Post by Perfect Storm on 2008-02-03
Ah, it's because it was written for 64-bit, search synaptic for ncurses.

---

### Post by Perfect Storm on 2008-02-03
I havn't tested the data thing yet. It was a quick guide on compiling the engine.

---

### Post by DoktorSeven on 2008-02-03
The betas have been simply terrible.  I've had more crashes and weirdness with those than anything, and they're simply a pain to compile, as you've seen.

Go find the 1.8.6 stable release and build it.  I should make a package for it (I have a checkinstall package, but doing it the right way is so much better), but if you want to build it yourself, you'll need a few SDL (-dev) dependencies and GCC-3.4 (install gcc-3.4 and g++-3.4), and build using EXPORT CC=gcc-3.4 and EXPORT CXX=g++-3.4.

---

### Post by MaximB on 2008-02-03
> **DoktorSeven said:**
> The betas have been simply terrible.  I've had more crashes and weirdness with those than anything, and they're simply a pain to compile, as you've seen.

Go find the 1.8.6 stable release and build it.  I should make a package for it (I have a checkinstall package, but doing it the right way is so much better), but if you want to build it yourself, you'll need a few SDL (-dev) dependencies and GCC-3.4 (install gcc-3.4 and g++-3.4), and build using EXPORT CC=gcc-3.4 and EXPORT CXX=g++-3.4.

It will be dependencies hell , I will wait for your package (32bit).
Please post it here as soon as you build it.

Thanks.

---

### Post by DoktorSeven on 2008-02-03
Okay, usual disclaimer for my packages applies here: if it ruins your system, destroys your plants, makes you pets sick, etc, don't blame me, use at your own risk, etc, etc, etc.  Tested them on my system, though, and it worked fine.

[Doomsday engine (deng) and gdoomsday frontend](http://sdcofer.googlepages.com/home)  [color=red]Edited:[/color] new download location.

These were both built on 7.10 Gutsy, so any other Ubuntu release might not work, I don't know.  Again, cross your fingers. :)

Edit: Oh, nothing makes any shortcuts by the way.  To run the frontend just run the executable **gdoomsday** and make desktop/menu shortcuts to that if you want.

---

### Post by MaximB on 2008-02-03
Thanks, I have found another package which is much larger for some reason (also for feisty).
Here : [http://skipgrube.ath.cx/skip/linux-packages.htm](http://skipgrube.ath.cx/skip/linux-packages.htm)

Now which one should I install ? 
And were do I put the WAD, textures and 3d model files ?

---

### Post by DoktorSeven on 2008-02-03
That version sounds like one of the 1.9.0 betas since it has the Snowberry launcher.  You can try it, but again, I've had bad luck with the 1.9.0 betas.

The WADs you can point to with one of the launcher programs like Snowberry on 1.9.0 or gdoomsday, so they can be put anywhere you want, though Doomsday does have a problem with paths with spaces in them, so avoid putting spaces in your path.

---

