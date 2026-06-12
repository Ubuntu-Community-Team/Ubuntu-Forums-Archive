---
title: "osmos doesnt run"
date: 2011-02-14
forum: Gaming &amp; Leisure
---

### Post by guine on 2011-02-14
So I just tried to install osmos and when I ran it loads to a blue screen with some circular designs on it and it says its loading music.  After a minute or so this stops and nothing else happens.  I tried reinstalling the game and all this did was make it load to the blue screen a little bit faster.  I also saw a thing about needing to change the font type using this
```
mv /opt/Osmos/Fonts/FortuneCity.ttf /opt/Osmos/Fonts/FortuneCity.ttf.bakcup
cp /usr/share/fonts/<fontyoulike.ttf> /opt/Osmos/Fonts/FortuneCity.ttf
```
But this has had no effect on what happens.  Has anyone else had this problem or have any idea how to fix it?

---

### Post by thatguruguy on 2011-02-14
have you tried running it from the terminal?

---

### Post by guine on 2011-02-14
The same thing happens in terminal.  This is what shows up in terminal
```
Log opened on Mon Feb 14 22:23:55 2011
Commandline: ./Osmos.bin32 
Preinitializing game: HEMI version 1.6.0 1314
Localization: using language "en"
Localization: loaded Osmos-en.loc
Arch: Intel(R) Pentium(R) 4 CPU 2.26GHz
OS: Linux 2.6.31-22-generic (#70-Ubuntu SMP Wed Dec 1 23:51:13 UTC 2010)
Using sound
Showing splash
Using fullscreen mode: 1024 x 768
Not using vsync
Initializing GLRenderDevice...
OpenGL version: 1.5.8 NVIDIA 96.43.13
Initializing game
Initializing GLRenderer...
Loading textures
Loading fonts
Backed up stats to Stats/Backup/Osmos_0003.sta
Initializing SoundSystem...
Initializing OpenAL
Getting OpenAL device list
Found 5 devices:
  Device 0: ALSA Software (3: OPENAL DEFAULT)
  Device 1: OSS Software (2: OSMOS DEFAULT)
  Device 2: PortAudio Software
  Device 3: PulseAudio Software
  Device 4: Wave File Writer
Pass 1: no valid device was specified (-1)
Pass 2: attempting device 1: "OSS Software"...
Creating OpenAL context
Opened device "OSS Software"
Device supports maximum 256 sources
Streaming music
Loading pre-splash sounds
Loading post-splash sounds
Killed
```

---

### Post by ELD on 2011-02-15
Report it to the Osmos forum, best place for it.

---

