---
title: "missing sounds in pingus and etracer"
date: 2008-06-24
forum: Gaming &amp; Leisure
---

### Post by angryfirelord on 2008-06-24
Whenever I play those two games, I can tell that some instruments aren't playing at all for the background music, so it has these "gaps" to it. Can anyone else confirm this issue?

Debugging for pingus didn't produce anything on startup.
```
master@agent-smith:~$ pingus --maintainer-mode
BasePath: /usr/games/../share/games/pingus/data/
Welcome to Pingus 0.7.2!
========================
data path:               /usr/games/../share/games/pingus/data/
language:                English (en)
font encoding:           iso-8859-1
sound support:           enabled
music support:           enabled
resolution:              800x600
fullscreen:              disabled

Manager: Loading driver 'sdl'
Manager: Loading driver 'core'

```
```
master@agent-smith:~$ pingus --debug=sound
Welcome to Pingus 0.7.2!
========================
data path:               /usr/games/../share/games/pingus/data/
language:                English (en)
font encoding:           iso-8859-1
sound support:           enabled
music support:           enabled
resolution:              800x600
fullscreen:              disabled

[Output] Initializing SDL audio
[Output] Initializing SDL_Mixer
[Output] PingusSoundReal: Playing music: /usr/games/../share/games/pingus/data//music/pingus-1.it
Manager: Loading driver 'sdl'
Manager: Loading driver 'core'

```
I also tried playing pingus-1.it through Totem and it sound fine, so it's not the file. I suspect it could be a problem with the SDL packages. Can anyone else confirm this issue?

---

### Post by RIchard James13 on 2008-06-26
My install of pingus also has missing musical instruments. I did not notice before because the music level is too low to hear on my system.

---

### Post by lykwydchykyn on 2008-08-31
I have this issue too, on only one of my machines though.  I've tried reinstalling the games, sdl-mixer, and installed any file I could find related to .it files (impulse tracker files).  I can't figure it out.

Anyone have an idea?

---

### Post by Jthulhu on 2010-10-19
I converted the .it files to .ogg using schism and audacity.
and edited the all the ".it"'s to ".ogg" in the level data files.

a bit of effort but it fixed it for me.

---

