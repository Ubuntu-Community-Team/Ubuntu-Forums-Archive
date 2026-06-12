---
title: "Enemy Territory, CS:S, Tremulous help"
date: 2006-08-24
forum: Gaming &amp; Leisure
---

### Post by yodaky on 2006-08-24
I have the abvove games installed.  I had Tremulous and CS:S installed and working fine.  When I installed ET I think something got "crossed" somewhere.  Now, when I run CS:S I run around like I am speed hacking and when I try to run Tremulous (or Mplayer 32bit) I get an error that says:


tremulous: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

ET DOES run however there is NO sound.  I have tried removing, changing, reinstalling the libsdl-1.2 drivers from the alsa based to the one that has all options enabled and back again multiple times.  However, it still does not work.

If I run et in the terminal I see:

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------

Can anyone offer advice on what else I should be trying to do?

---

### Post by qrm on 2006-08-24
in wiki there is a solution for your problem with ET

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

---

### Post by yodaky on 2006-08-24
Thanks, any thoughts on how to fix my libSDL issues?

---

### Post by qrm on 2006-08-24
you could look around with synaptic and search for something that looks like libsdl 1.2 ;)

---

