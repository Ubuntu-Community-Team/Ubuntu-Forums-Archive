---
title: "Cannot get Quake 2 to play"
date: 2008-09-21
forum: Gaming &amp; Leisure
---

### Post by GSZX1337 on 2008-09-21
I am installing every game that's Linux native that I own and of course, I am trying to install my Quake games. I have tried the [Loki installer]("http://www.liflg.org/?catid=6&gameid=55") and [this]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake&back=HOWTO+INDEX+Linux+Games") tutorial. I have also tried the Quake2-data in the repos, but I don't know what to do with it after I download it.

Any help will be appreciated.
~GSZX1337

---

### Post by GSZX1337 on 2008-09-22
bumpy

---

### Post by chungy on 2008-09-22
Might want to check this thread: [http://ubuntuforums.org/showthread.php?t=926486](http://ubuntuforums.org/showthread.php?t=926486)

---

### Post by GSZX1337 on 2008-09-27
I recently attempted to install Quake 2 again. I actually managed to get a terminal out put:


```
gszx1337@GMan:~$ bash '/home/gszx1337/quake2.sh' 
Error loading new keyboard description
-> Red  1.000, Green  1.000, Blue  1.000
<- Red  1.300, Green  1.300, Blue  1.300
Quake 2 -- Version 3.21+r0.16
Added packfile ./baseq2/pak0.pak (3307 files)
Added packfile ./baseq2/pak1.pak (279 files)
Added packfile ./baseq2/pak2.pak (2 files)
Added packfile ./baseq2/pak10.pak (806 files)
Added packfile ./baseq2/pak11.pak (47 files)
Added packfile ./baseq2/pak12.pak (79 files)
Added packfile ./baseq2/pak13.pak (16 files)
Added packfile ./baseq2/pak14.pak (46 files)
Added packfile ./baseq2/pak16.pak (30 files)
Added packfile ./baseq2/pak17.pak (22 files)
Added packfile ./baseq2/pak19.pak (13 files)
Added packfile ./baseq2/maxpak.pak (40 files)
using /home/gszx1337/.quake2/baseq2/ for writing
execing default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Couldn't open SDL audio: No available audio device
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so") failed: No such file or directory
Refresh failed
recursive shutdown
Error: Couldn't fall back to software refresh!
-> Red  1.300, Green  1.300, Blue  1.300
<- Red  1.000, Green  1.000, Blue  1.000

```

---

### Post by Brebs on 2008-09-27
Use the forum's Search button.

See [kmquake2](http://ubuntuforums.org/showthread.php?t=890091).

---

