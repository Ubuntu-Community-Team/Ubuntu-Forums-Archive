---
title: "loki's quake2"
date: 2008-08-30
forum: Gaming &amp; Leisure
---

### Post by Stargazer989 on 2008-08-30
ive installed loki's linux port of quake2 by typing './quake2' in the terminal... but i get this error:
> Quake 2 -- Version 3.21+r0.16
Added packfile ./baseq2/pak10.pak (806 files)
Added packfile ./baseq2/pak11.pak (47 files)
Added packfile ./baseq2/pak12.pak (79 files)
Added packfile ./baseq2/pak13.pak (16 files)
Added packfile ./baseq2/pak14.pak (46 files)
Added packfile ./baseq2/pak16.pak (30 files)
Added packfile ./baseq2/pak17.pak (22 files)
Added packfile ./baseq2/pak19.pak (13 files)
Added packfile ./baseq2/maxpak.pak (40 files)
using /home/stargazer/.quake2/baseq2/ for writing
couldn't exec default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
ALSA snd error couldn't set params (Invalid argument).
------- Loading ref_softx.so -------
LoadLibrary("./ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx


---

### Post by Stargazer989 on 2008-08-30
hmmm... seems when i run it via 'quake2' in the Terminal i get:
> dirname: missing operand
Try `dirname --help' for more information.
Error loading new keyboard description
-> Red  1.000, Green  1.000, Blue  1.000
<- Red  1.300, Green  1.300, Blue  1.300
/home/stargazer/bin/quake2: 64: ./sdlquake2: not found
-> Red  1.300, Green  1.300, Blue  1.300
<- Red  1.000, Green  1.000, Blue  1.000
stargazer@PR-DE-UK-JP-CA:~/quake2$ 


---

### Post by Brebs on 2008-08-31
That's an ancient version anyway. The best Quake2 version in Linux currently is [kmquake2](http://ubuntuforums.org/showthread.php?t=890091).

---

### Post by RIchard James13 on 2008-09-01
Quake (any version) can be divided into two main parts
A) the data files
B) the engine that plays the game

since the engine is under the GPL many people have made improved engines. If you have the old Loki engine you can replace it with a modern engine and still use your data files from the Loki CD.

---

