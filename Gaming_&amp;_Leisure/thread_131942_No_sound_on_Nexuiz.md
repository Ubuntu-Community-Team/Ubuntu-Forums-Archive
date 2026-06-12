---
title: "No sound on Nexuiz"
date: 2006-02-17
forum: Gaming &amp; Leisure
---

### Post by holobyted on 2006-02-17
Hey all... I tried playing Nexuiz and it runs fine, the graphics are superb. However, I can't get my sound to work at all.


The SDL version just about refuses to work, even with the export SDL_NOsomething="1" trick, and the GLX version gives me crappy sound and doesn't seem to respect the -sndspeed parameter. Already tried recompiling.


Currently using Ubuntu 5.10 on an 9NDA3J motherboard - onboard Realtek AC97 chip. Using ALSA.


Hope you guys can help

---

### Post by Asraniel on 2006-02-17
i start nexuiz with:
./nexuiz-glx -sndspeed 48000 -sndstereo

with sdl i have no sound and without the sndspeed parameter the sound is broken.

---

### Post by holobyted on 2006-02-17
Ironic... I tried that last night and it didn't work. Go figure...

Thanks :p Is there a way to fix the SDL issue? I've heard most games use SDL nowadays.

---

### Post by polpak on 2006-02-17
For issues with SDL and sound....

Try installing libsdl1.2debian-all or libsdl1.2debian-alsa.. I think the only one installed by default is libsdl1.2debian-oss, and on my system oss doesn't really work very well (or at all)

---

### Post by holobyted on 2006-02-17
Tried that last night... I was getting "can't create mcop directory" when opening Nexuiz.

---

### Post by Asraniel on 2006-02-18
for nexuiz tech support, try the nexuiz forums, with the search function you will perhaps directly find the solution

---

### Post by RuleMaker on 2008-08-08
It's because you don't have appropriate libsdl, go to synaptic and search for "SDL".
For example, if your default audio driver is pulseaudio then you need to install the "libsdl1.2debian-pulseaudio" if it's OSS then "libsdl1.2debian-oss" if it's ALSA then "libsdl1.2debian-alsa" and so on...

---

### Post by detrate on 2008-08-09
I had the same problem, this thread should help clarify: [http://www.alientrap.org/forum/viewtopic.php?p=37646#37646](http://www.alientrap.org/forum/viewtopic.php?p=37646#37646)

---

