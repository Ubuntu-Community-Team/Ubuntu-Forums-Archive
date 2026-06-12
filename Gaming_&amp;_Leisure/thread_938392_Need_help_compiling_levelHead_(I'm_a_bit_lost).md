---
title: "Need help compiling levelHead (I'm a bit lost)"
date: 2008-10-04
forum: Gaming &amp; Leisure
---

### Post by Mad_Gouki on 2008-10-04
Sorry for being a noob when it comes to this, but I really need some help.  Perhaps this is the wrong forum to ask for this type of help in, if it is, could a moderator please move it or could you recommend which forum to post this in?

With that said, here is what I'm trying to do.
I found this game called levelHead:
[http://julianoliver.com/levelhead](http://julianoliver.com/levelhead)
Check out the videos
[http://www.youtube.com/watch?v=5ks1u0A8xdU](http://www.youtube.com/watch?v=5ks1u0A8xdU)
it looks awesome, right?

It was designed to be run on ubuntu or debian, and the developer claims to run it on ubuntu 7.04 and 7.10.

I have the required camera(2 that are compatible, actually).  Many cameras should work with this "game"
The instructions are as follows
[http://selectparks.net/~julian/levelhead/install](http://selectparks.net/~julian/levelhead/install)
> **Compilation steps:**

  **1. Install GStreamer**

  **2. Compile ARToolkit.**

       If using a Linux UVC supported camera, when running ./Configure be sure to choose       'GStreamer' as the video capture driver.
     If using the Sony Eyetoy, when running ./Configure be sure to choose 'Video4Linux' as the video capture driver (don't choose the option Video4Linux Sony Eyetoy). You will probably need to also comment out the ARTOOLKIT_CONFIG environment variable in /path/to/levelHead/trunk/bin/run.sh
      There is no need to install ARToolkit system-wide. Just run make after       this point.
 **3. Compile ARTookitPlus**

     Follow the steps in the INSTALL file of ARToolkitPlus
 **4. Install other dependencies above.**

     NOTE: I use uvcdynctrl from Logitech's libwebcam in /path/to/levelHead/trunk/bin/start_levelHead.sh to focus the camera.       This greatly improves performance of the tracking so it's reccommended       you install it (system wide) too. **5. Compile levelHead.**

     cd /path/to/levelHead/trunk/src/levelHead/bin
    edit the path_config.sh to match the paths you have for ARToolkit and       ARToolkitPlus.
 Edit the path in /path/to/levelHead/trunk/bin/build.sh to point to ARToolkit
      sh build.sh to build


I can get to step 3, this is where I have issues.

I need help figuring out how to configure ARToolkitPlus, and then the settings to change in the levelHead config files.

the ARToolkitPlus install file states:
```
Install instructions for Linux:
===============================

Remarks:
--------

The make environment for Linux is based on Qt's qmake system.
Please install qmake before compiling ARToolKitPlus!

Compile Steps:
--------------

- Modify build/linux/options.pro to your needs
- Set ARTKP environment variable to source tree

  for bash: export ARTKP='<path_to_artoolkitplus_source_tree>'
  for tcsh: setenv ARTKP '<path_to_artoolkitplus_source_tree>'

- Start compilation with

  make

- You should end up with

  ./lib ... ARToolKitPlus shared libraries
  ./bin ... 
        simple   ... Sample program
        idpatgen ... For generating ID markers

- For executing, do not forget to update your LD_LIBRARY_PATH
```

I really don't know what this stuff means.
I can post the config files if that would help.  I'm sure it's something small that has to be changed, I'm just not sure all of the little things to set.
Any help would be appreciated!

---

### Post by Vadi on 2008-10-04
Well, try posting the options.pro file that's in build/linux/ to start with.

Though, I hope someone makes .debs for this.

---

### Post by Mad_Gouki on 2008-10-04
I'll write a tutorial if I figure it out, perhaps somebody can make a .deb based on that.
As for the .pro file, it is as follows
```
# ############################################################
#
# Linux project definitions for ARTookKitPlus
#

###
# change target install path

INSTALL_PATH = /usr/local
isEmpty(PREFIX) { PREFIX = $$INSTALL_PATH }
isEmpty(LIBDIR) { LIBDIR = $$PREFIX/lib }

###
# choose between debug and release mode

CONFIG        = debug
#CONFIG        = release

###
# add additional optimization flags (platform-specific)

equals(ARCH, x86_64) {
  # options for AMD64
}
else {
#  QMAKE_CXXFLAGS      = -mtune=pentium4 -march=pentium4 -msse2 -msse -fpermissive
  QMAKE_CXXFLAGS      = -mtune=pentium4 -march=pentium4 -msse2 -msse 
}


# ############################################################
# DO NOT EDIT BELOW THIS LINE !!!
# ############################################################

VERSION         = 2.0.2

UNAME           = $$system(uname -r)
#message("Found kernel ($$UNAME) ...")

LANGUAGE = C++

debug {
  OBJECTS_DIR     = $$(ARTKP)/build/linux/debug
}

release {
  OBJECTS_DIR     = $$(ARTKP)/build/linux/release
}

DEPENDPATH      += $$(ARTKP)/include

INCLUDEPATH     += $$(ARTKP)/include

LIBS            += -L$$(ARTKP)/lib

# ############################################################
```The error I get when running make after qmake is as follows
```
alex@alex-laptop:~/Videos/ARToolKitPlus_2.1.1$ make
cd src && qmake src.pro -o Makefile
Cannot find directory: /build/linux
Project MESSAGE: Building ARToolKitPlus in release mode ...
cd src && make -f Makefile
make[1]: Entering directory `/home/alex/Videos/ARToolKitPlus_2.1.1/src'
g++ -c -pipe -Wall -W -O2 -D_REENTRANT -fPIC  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/share/qt3/include -o MemoryManager.o MemoryManager.cpp
MemoryManager.cpp:41:41: error: ARToolKitPlus/MemoryManager.h: No such file or directory
MemoryManager.cpp:51: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
MemoryManager.cpp:54: error: expected constructor, destructor, or type conversion before &#8216;void&#8217;
MemoryManager.cpp:61: error: &#8216;ARTOOLKITPLUS_API&#8217; does not name a type
MemoryManager.cpp: In function &#8216;void ARToolKitPlus::artkp_Free(void*)&#8217;:
MemoryManager.cpp:78: error: &#8216;memManager&#8217; was not declared in this scope
make[1]: *** [MemoryManager.o] Error 1
make[1]: Leaving directory `/home/alex/Videos/ARToolKitPlus_2.1.1/src'
make: *** [sub-src] Error 2

```The root folder is extracted from the zip file at /home/alex/Videos/ARToolKitPlus_2.1.1/

Am I missing dependencies?

This error about the location of these MemoryManager sources is a bit mind boggling from my perspective.

also, my friend said to use qmake with these options
&#65279;[SIZE=3]qmake -o Makefile artoolkitplus.pro[/SIZE]

---

### Post by DoktorSeven on 2008-10-04
Did you do the step where it told you to set an environment variable:

> - Set ARTKP environment variable to source tree

  for bash: export ARTKP='<path_to_artoolkitplus_source_tree>'


so you'd type something like:
```

export ARTKP='/home/alex/Videos/ARToolKitPlus/' 

```
or wherever you have the source of the code (edited, misread the instructions, sorry).

The only thing that I would change in the .pro file is to change the mode to Release:

```

#CONFIG        = debug
CONFIG        = release

```
(note the change of location of the #)

Good luck.

---

### Post by Mad_Gouki on 2008-10-05
DoktorSeven, I've done both of those things, it still gives the same errors. :(

---

### Post by Vadi on 2008-10-05
It should be looking for "build/linux" not "/build/linux". The / in front implies that it starts at your root folder (like /home/alex starts at the beginning too).

---

### Post by Mad_Gouki on 2008-10-05
looks like copying all the files into the /usr/share/qt3 folder gets rid of some of the errors... really odd, i shouldn't have to do this
```
alex@alex-laptop:/usr/share/qt3$ sudo make
cd src && make -f Makefile
make[1]: Entering directory `/usr/share/qt3/src'
test -d /lib/ || mkdir -p /lib/
rm -f libARToolKitPlus.so.1.0.0 libARToolKitPlus.so libARToolKitPlus.so.1 libARToolKitPlus.so.1.0
g++ -shared -Wl,-soname,libARToolKitPlus.so.1 -o libARToolKitPlus.so.1.0.0 MemoryManager.o DLL.o rpp.o rpp_quintic.o rpp_vecmat.o rpp_svd.o librpp.o Profiler.o FixedPoint.o   -L/usr/share/qt3/lib -lqt-mt -lpthread 
/usr/bin/ld: cannot find -lqt-mt
collect2: ld returned 1 exit status
make[1]: *** [/lib/libARToolKitPlus.so.1.0.0] Error 1
make[1]: Leaving directory `/usr/share/qt3/src'
make: *** [sub-src] Error 2

```

edit:
I think i got it, installed &#65279;[SIZE=3]libqt3-mt-dev
[/SIZE]from repos and it compiled without error, had a few warnings (but they were mainly of the mundane unused variable variety).

I'll update on how the next step in making levelhead goes.  If i figure it out, i'll write a tutorial for it so that someone can hopefully make a deb or script or something.  Here's hoping!

---

### Post by Mad_Gouki on 2008-10-06
edit:
oh
my
god
So... it's like this:  The game built, it runs, I'm not going to hook up a webcam right now to test it, but I'm pretty sure it will work (it draws a white screen with no camera attached).
Success in that

The thing is, if you actually want to make it for yourself, you will be run through something we call dependency hell.  The simple solution to that is to FIRST (THE VERY FIRST STEP) add the gutsy repositories to your synaptics repo list.  You will need the versions of things that are a real pain to compile, or even FIND.  Once you have the gutsy repo list, it is fairly painless to find the dependencies and install them.

I can make a little (big) tutorial for this, which should be enough to get the most determined a compiled game.
The biggest pain is figuring out how to get ARToolkitPlus working, I stuck it in usr/share/qt3 to compile it, because I am lazy and it seemed to work.
Every little thing you compile for this has a list of dependencies.  I wish the rest of you the best of luck.  I'll let you know how it goes with actually trying to play it.

---

### Post by ritzdank on 2008-10-06
hi Mad_Gouki,

Thanks for opening this thread. I was also trying to build levelhead but to no avail...

> looks like copying all the files into the /usr/share/qt3 folder gets rid of some of the errors...

Did you simply copy all files/folders from ARToolkitPlus/src into /usr/share/qt3? Did you set $ARTKP to /home/user/src/ARToolkitPlus ?

i have libqt3-mt-dev definitely installed, but i am running into the same compile errors again:

```
cd src && make -f Makefile
make[1]: Entering directory `/home/user/src/ARToolkitPlus/src'
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT -fPIC  -DQT_NO_DEBUG -DQT_THREAD_SUPPO                                                                                       RT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/i                                                                                       nclude/qt3 -o MemoryManager.o MemoryManager.cpp
MemoryManager.cpp:41:41: error: ARToolKitPlus/MemoryManager.h: No such file or d                                                                                      irectory
```

I am already working on Intrepid, so not sure whether i should add gutsy repos into my synaptics list?!

---

### Post by Mad_Gouki on 2008-10-06
You need the EXACT versions of the things that guy is using.  the gutsy repo's have those exact versions.
I copied all the files from the ARToolkitPlus folder and merged them into the qt3 folder
so src goes into the pre-existing qt3 src folder, and so on.
It's a messy way to do it, and it could have something to do with my set-up, I'm not really sure.

The game is still not working, but I'm hoping that I can get the uvc driver working with one of my cameras (I have 4, one of them has to work!), and then figure it out from there.

The creator of the game gives fairly basic instructions for compiling.

but that error that you posted, I fixed it by copying the files as described above (2nd sentence).  Like I said previously in this thread, we shouldn't have to do this.  To be honest, I don't remember what I set the export variable to :(  It was either the /home/alex/Videos/ARToolkitPro folder, or the /usr/share/qt3 folder, I'm pretty sure it was the latter
```
export ARTKP='/usr/share/qt3'
```

---

### Post by sven78 on 2008-10-22
Hi!

i allready had a compiled Version on Ubuntu 8.04.1, but now on 8.10 i can not compile it again.

I have the qt3 dev package installed.
I have set the PATH variable.
I have adjusted the options.pro file to match my CPU.

But i get this error:

make
make: *** No rule to make target `/usr/lib/qt3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.

Okay, then i recreated the Makefile with:
qmake-qt3 -o Makefile artoolkitplus.pro

But then my compile process looks like this:
```
make
cd src && qmake src.pro -o Makefile
Project MESSAGE: Building ARToolKitPlus in debug mode ...
cd src && make -f Makefile
make[1]: Entering directory `/usr/local/src/atkplus-2.1.1/src'
g++ -c -O0 -fPIC   -I/usr/share/qt3/mkspecs/default -I. -I../include -o ../build/linux/debug/MemoryManager.o MemoryManager.cpp
g++ -c -O0 -fPIC   -I/usr/share/qt3/mkspecs/default -I. -I../include -o ../build/linux/debug/DLL.o DLL.cpp
g++ -c -O0 -fPIC   -I/usr/share/qt3/mkspecs/default -I. -I../include -o ../build/linux/debug/rpp.o librpp/rpp.cpp
librpp/rpp.cpp: In function 'void rpp::robust_pose(rpp::real_t&, rpp::mat33_t&, rpp::vec3_t&, const rpp::vec3_array&, const rpp::vec3_array&, rpp::options_t)':
librpp/rpp.cpp:753: error: 'memcpy' was not declared in this scope
make[1]: *** [../build/linux/debug/rpp.o] Error 1
make[1]: Leaving directory `/usr/local/src/atkplus-2.1.1/src'
make: *** [sub-src] Error 2
```

Any idea what i can do about this?

---

### Post by sven78 on 2008-10-24
By adding these lines, librpp compiled well:

rpp_vecmat.h:#include <string.h>
rpp_vecmat.h:#include <stdlib.h>
rpp_vecmat.h:#include <stdio.h>

rpp.h:#include <string.h>
rpp.h:#include <stdlib.h>


But i have a warning for you!
I did a **sudo make clean**. It came out that for some reason the file src/Makefile contained the command:
**rm -f /lib/***

#-o :shock: ](*,) :sad:

I had to recover my installation from a backup.

---

### Post by pvinis on 2008-11-05
I get this error

```
error: CPU you selected does not support x86-64 instruction set
```
what is that?
shoud I change the options.pro file? I havent changed it.

I run ubuntu 8.10 x64 on intel.
I have everything else installed fine, except ARToolPlus.

little help please?

EDIT: nevermind.. I did it! but now i cannot build tha game.. I do sh build.sh but it said
```
build.sh: 5: bakefile: not found
make: GNUmakefile: No such file or directory
make: *** No rule to make target `GNUmakefile'.  Stop.

```

now what?

---

### Post by pvinis on 2009-02-04
i finally managed to compile everything in 32bit 7.10, but now when I start the game, all I see is a white screen saying place the red cube in the box to start or something like that..

my camera (isight) works with gstreamer, cheese and ekiga, but I cannot figure out what's wrong with the game..


anyone?

---

### Post by derflooh on 2009-03-12
I also managed to compile it, but when i try to start it ist says

```
CullSettings::readEnvironmentalVariables()
Opened DynamicLibrary osgart_artoolkit.so
VideoManager::createVideoFromPlugin(plugin): Plugin 'osgart_artoolkit' successfully instantiated a video handler
Added a osgART::GenericVideo with ID:0 to the VideoManager
Opened DynamicLibrary osgart_artoolkitplus_tracker.so
osgART::TrackerManager::addTracker(tracker): Added tracker with ID 0
Field 'threshold' = 150
video open....
using ARTOOLKIT_CONFIG
config=v4l2src device=/dev/video0 use-fixed-fps=false ! ffmpegcolorspace ! capsfilter caps=video/x-raw-rgb,bpp=24,width=960,height=720 ! identity name=artoolkit ! fakesink
Using supplied video config string [v4l2src device=/dev/video0 use-fixed-fps=false ! ffmpegcolorspace ! capsfilter caps=video/x-raw-rgb,bpp=24,width=960,height=720 ! identity name=artoolkit ! fakesink].
libARvideo: GStreamer 0.10.21

** ERROR **: libARvideo: failed to put GStreamer into PAUSE state!

aborting...
Aborted
```

//EDIT: The problem was the wrong resolution in run.sh at ARTOOLKIT_CONFIG. I changed it from 960x720 to 640x480 (width=640,height=480). Now the game starts. But all rooms are black.
[[IMG]http://img519.imageshack.us/img519/5839/bildschirmfoto.th.png[/IMG]](http://img519.imageshack.us/my.php?image=bildschirmfoto.png)

---

