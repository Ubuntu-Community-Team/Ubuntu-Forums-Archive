---
title: "Ugly sound with sdlmame and karmic"
date: 2009-12-07
forum: Gaming &amp; Leisure
---

### Post by yodaz on 2009-12-07
Hi,

I'm using sdlmame on a karmic, with libsdl1.2debian-pulseaudio installed, and the sound is ugly. I've tried to set the sdl audio driver to "pulse" in sdlmame.ini but it didn't work, the sound is still ugly.

The sound works well with all other apps (kaffeine, mplayer, amarok ...), even those who use SDL (mednafen, frozen-bubble ...)

My audio chipset is a VIA AC97, here is the lspci output :

00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)

I've joined my sdmame.ini file, and the log output when I launch sdlmame.

Is it a bug ? What can I do to fix it ?

Thanks in advance.

---

### Post by mocha on 2009-12-17
Install "libsdl1.2debian-all" instead and then set the SDL audio driver to "esd".

---

### Post by yodaz on 2009-12-18
Hi and thank you for your answer. I've already tried what you say, and I'v no sound, even with starting sdlmame with -ad esd option.

Anyway, my laptop is dead (hard disk failure), so I'm waiting to get my new machine. It's an Intel ET5300 with Intel GMA 3100 video chipset.

I hope it will work better with sdlmame.

---

