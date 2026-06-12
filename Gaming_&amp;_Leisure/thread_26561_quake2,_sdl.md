---
title: "quake2, sdl"
date: 2005-04-13
forum: Gaming &amp; Leisure
---

### Post by tont on 2005-04-13
tont@laf:/usr/games/quake2$ quake2
-> Red  1.000, Green  1.000, Blue  1.000
<- Red  1.300, Green  1.300, Blue  1.300
Quake 2 -- Version 3.21+r0.16
Added packfile ./baseq2/pak10.pak (806 files)
Added packfile ./baseq2/pak11.pak (47 files)
Added packfile ./baseq2/pak12.pak (79 files)
Added packfile ./baseq2/pak13.pak (16 files)
Added packfile ./baseq2/pak14.pak (46 files)
Added packfile ./baseq2/pak16.pak (30 files)
Added packfile ./baseq2/pak17.pak (22 files)
Added packfile ./baseq2/pak19.pak (13 files)
Added packfile ./baseq2/maxpak.pak (40 files)
using /home/tont/.quake2/baseq2/ for writing
couldn't exec default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
Couldn't open SDL audio: No available audio device
------- Loading ref_softsdl.so -------
LoadLibrary("./ref_softsdl.so")
SDL Joystick not initialized, trying to init...
Trying to start-up joystick...
No joysticks available
recursive shutdown
Error: Couldn't load pics/colormap.pcx
-> Red  1.300, Green  1.300, Blue  1.300
<- Red  1.000, Green  1.000, Blue  1.000
tont@laf:/usr/games/quake2$


what should i do to get q2 running ?
totally mindless after yesterdays googeldoo..

---

### Post by artinla on 2005-04-14
try killing esd before you run the game.

Also,  check the permissions on /dev/dsp .

It is looking to ref_softsdl.so for an audio driver,  do you have that file in your path?  It is probably a symlink.  What is the link pointing to on your system?

Art

---

### Post by tont on 2005-04-15
if i kill esd, it says

tont@laf:~$ quake2
-> Red  1.000, Green  1.000, Blue  1.000
<- Red  1.300, Green  1.300, Blue  1.300
Quake 2 -- Version 3.21+r0.16
Added packfile ./baseq2/pak10.pak (806 files)
Added packfile ./baseq2/pak11.pak (47 files)
Added packfile ./baseq2/pak12.pak (79 files)
Added packfile ./baseq2/pak13.pak (16 files)
Added packfile ./baseq2/pak14.pak (46 files)
Added packfile ./baseq2/pak16.pak (30 files)
Added packfile ./baseq2/pak17.pak (22 files)
Added packfile ./baseq2/pak19.pak (13 files)
Added packfile ./baseq2/maxpak.pak (40 files)
using /home/tont/.quake2/baseq2/ for writing
couldn't exec default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("./ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx
-> Red  1.300, Green  1.300, Blue  1.300
<- Red  1.000, Green  1.000, Blue  1.000
tont@laf:~$

 :???:

---

### Post by yusufk on 2005-04-15
If u search for "quake2", you should find:

[http://ubuntuforums.org/showthread.php?t=22920](http://ubuntuforums.org/showthread.php?t=22920)

which should sort it out!

---

### Post by tont on 2005-04-17
actually it didn't work for me..

---

### Post by yusufk on 2005-04-18
Have you tried the suggested reply? (i.e. create the file)

---

### Post by tont on 2005-04-18
yes, but it still doesn't work..

---

### Post by tont on 2005-04-20
bumping up without any result yet :x

---

### Post by olegboleg on 2006-02-01
i ahd this problem. i fixed it (since i am a linux rookie, i dont know any better ways) by copying all game datafiles tro ->usr/lib/games/quake2/
specialy the pak0.pak (wich contains the msisng colormap.pcx wich you need to start the game) wich is in the /baseq2/ directory of quake2. then quake2 started for me.

ole
(if i didint explain it good, reply ;)

---

