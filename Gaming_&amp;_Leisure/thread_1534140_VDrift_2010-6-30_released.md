---
title: "VDrift 2010-6-30 released"
date: 2010-07-19
forum: Gaming &amp; Leisure
---

### Post by portets on 2010-07-19
excuse me if it's been posted already.

some new features:
* rewritten physics engine that fixes many bugs, improves performance,  and vastly improves simulation accuracy
* new deferred rendering engine that supports normal maps, true HDR  rendering, screen-space ambient occlusion, and soft particles
* meshes for brake rotors, better wheel and tire meshes
* bugfixes and tweaks to control input management
* new sounds

the track rouen is the only place with normal maps so far. and they are unfinished.

(taken from [COLOR=Purple][here]("http://vdrift.net/article.php?story=20100714200428239")[/COLOR], the vdrift news post)
click the above link for a detailed changelog. also, [COLOR=Purple][here]("http://www.phoronix.com/scan.php?page=article&item=vdrift_2010_june&num=1")[/COLOR]'s a phoronix news article covering it.

remember, it's just a development release so it may be buggy.

now a couple of screenshots:

[ATTACH]163894[/ATTACH]

[ATTACH]163895[/ATTACH]

there is only a source package right now, so you'll have to compile it yourself. i'd package a .deb, but i don't know how yet.

download the source [here]("https://sourceforge.net/projects/vdrift/files/vdrift/vdrift-2010-06-30/vdrift-2010-06-30.tar.bz2/download")

**edit: **getdeb made a package [here]("http://www.playdeb.net/software/VDrift")

to fulfill dependencies, open a terminal and type:
```

sudo apt-get install g++ scons libsdl-gfx1.2-dev libsdl-image1.2-dev libsdl-net1.2-dev libvorbis-dev libglew-dev libasio-dev libboost-dev

```then to compile, open a terminal in vdrifts base directory:
```
scons release=1
```or for 64-bit machines:
```
scons arch=a64 release=1
```

---

### Post by alanwalterthomas on 2010-08-07
Having trouble. I ran:

alan@desktop:~/Downloads/vdrift-2010-06-30$ scons arch=a64 release=1 -j 4

(-j 4 to compile faster on a 4 core cpu)

But i got ~/Downloads/vdrift-2010-06-30/binaries/linux32

What went wrong so I got linux32 (32-bit?) when I specified arch=a64?

Also, I tried ./vdrift in the linux32 directory, but I got

./vdrift: error while loading shared libraries: libGLEW.so.1.5: cannot open shared object file: No such file or directory

Any idea what's wrong here? I didn't get any obvious error messages during compilation & a google search of the error only shows a couple useless results that are more than a year old.

---

### Post by portets on 2010-08-07
oh, i left out the last couple of steps. sorry :oops:

the binary should be in the "build" directory. copy and paste it to vdrift's main directory.

edit: forgot to mention, getdeb recently made a package for this release. [here]("http://www.playdeb.net/software/VDrift")

---

### Post by Naiki Muliaina on 2010-08-07
I have always found this game so utterly bad its utterly unplayable... The handling on the cars is just so terrible... Has it improved at all in the new release?

---

### Post by portets on 2010-08-08
> **Naiki Muliaina said:**
> I have always found this game so utterly bad its utterly unplayable... The handling on the cars is just so terrible... Has it improved at all in the new release?

the physics engine was rewritten and moved to bullet in this release. i'm pretty sure it's not completely finished, but i personally find this release more playable than past releases. car physics feel quite a bit more realistic to me

---

### Post by Naiki Muliaina on 2010-08-08
Gave it another go, blah, they should ask the Trigger guys if they can help with the car physics engine. That would make it playable.

---

### Post by alanwalterthomas on 2010-08-08
I looked in the build directory, there's a vdrift executable, but this happens:
alan@desktop:~/vdrift-2010-06-30/build$ ./vdrift 
INFO: Multi-processor system detected.  Run with -multithreaded argument to enable multithreading (EXPERIMENTAL).
INFO: Starting VDrift: 2010-08-08-full, Version: exported, O/S: Unix-like
INFO: Home directory: /home/alan
INFO: Settings file: /home/alan/.vdrift/VDrift.config (does not exist, will be created)
INFO: Data directory: /usr/local/share/games/vdrift/data
      DATA_DIR: /usr/local/share/games/vdrift/data
INFO: Log file: /home/alan/.vdrift/log.txt
INFO: The last VDrift startup was unsuccessful.
      Settings have been set to failsafe defaults.
      Your original VDrift.config file was backed up to VDrift.config.backup
INFO: SDL initialization successful
INFO: SDL video query was successful
INFO: Disabling antialiasing
INFO: Display change was successful: 800x600x16 16z fullscreen=0
INFO: Video card information:
      Vendor: ATI Technologies Inc.
      Renderer: ATI Radeon HD 4600 Series
      Version: 3.2.9756 Compatibility Profile Context
      Maximum texture size: 8192
      Maximum varying floats: 64
      Using GLEW 1.5.2
INFO: Maximum color attachments: 8
INFO: Maximum draw buffers (1 required): 8
INFO: Disabling shaders
ERROR: Unable to open graphics config file: /usr/local/share/games/vdrift/data/shaders/render.conf.noshaders
ERROR: Error loading non-shader render configuration file: /usr/local/share/games/vdrift/data/shaders/render.conf.noshaders
vdrift: src/graphics.cpp:697: void GRAPHICS_SDLGL::DisableShaders(const std::string&, std::ostream&): Assertion `0' failed.
SIGABRT detected, releasing the mouse
Aborted

It looks like I'm missing a graphics config file, but I don't know where to get it & I don't want to screw anything up. Any ideas? Thanks,

ALAN

---

### Post by portets on 2010-08-09
looks like the executable is still in the build directory. just copy and paste it into the folder that contains the data, build, source, etc. folders.

---

### Post by alanwalterthomas on 2010-08-10
Ok, putting vdrift in the parent directory worked. Then I deleted the folder after a painful lap.

---

