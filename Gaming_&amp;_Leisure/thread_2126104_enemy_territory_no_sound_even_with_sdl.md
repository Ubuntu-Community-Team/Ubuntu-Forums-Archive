---
title: "enemy territory no sound even with sdl"
date: 2013-03-16
forum: Gaming &amp; Leisure
---

### Post by akimb0 on 2013-03-16
Hey guys,

got a problem with my good old enemy territory. 
I dont change anything on my system hardwareside but after an update via synaptics i dont get any sound working in ET.

I start ET with sdl-hack (some of you may know this) like 

```
./et-sdl-sound
```
where ALSA is my systemwide sound

This is what i get from my terminal:

```
------- sound initialization -------
SDL audio driver initializing...
SDL_Init(SDL_INIT_AUDIO) failed: SDL not built with audio support
------------------------------------

```

Why is SDL not built with audio support????

---

### Post by akimb0 on 2013-03-16
Well got it working.

The Problem seems to be coming with steam installed to my system! 
Steam with the game "Bastion" bring its own libSDL which are installed to ```
/home/YOURUSER/.local/share/Steam/SteamApps/common/Bastion/Linux/lib/libSDL-1.2.so.0
```
This one broke my audio support in ET.

If youre running into the same problem simply edit your et-sdl-sound, find the line 
```

# libSDL.so
#
# You can set this in LIBSDL environment variable
# LIBSDL=""
```

and change the last line to

```

# libSDL.so
#
# You can set this in LIBSDL environment variable
# LIBSDL="/usr/and/the/path/to/your/system/libSDL"

```

For example im running UbuntuStudio and needed to replace the line with 

```

LIBSDL="/usr/lib/i386-linux-gnu/libSDL-1.2.so.0"

```

---

