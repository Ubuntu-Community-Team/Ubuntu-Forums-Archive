---
title: "Fix RTCW, ET sound on Karmic x86_64 without using et-sdl-sound.so"
date: 2009-11-13
forum: Gaming &amp; Leisure
---

### Post by mullens101 on 2009-11-13
I'm running Ubuntu 9.10 (Karmic) x86_64.  I had been trying to use et-sdl-sound.so with RTCW.  I could get some really crackly sound using the et-sdl-sound.so hack and SDL_AUDIODRIVER set to "alsa" in the initialization script, but A: the sound was horrible and B: the game completely hung on exit (in et-sdl-sound.so, the calls to __SDL_CloseAudio would lock the game).

After a bunch of research, trying to hack and re-compile and failing, I finally have sound working well.  Here are the steps I used.

1.  Create a launcher script that has the following (The big difference here from the et-sdl-sound.so hack is the LD_PRELOAD line ... don't use et-sdl-sound.so, instead use "/usr/lib32r/libpulsedsp.so"):

export ETSDL_SDL_LIB="/usr/lib32/libSDL-1.2.so"
export SDL_AUDIODRIVER="alsa"
export LD_PRELOAD="${LD_PRELOAD}:/usr/lib32r/libpulsedsp.so"
cd /usr/local/games/wolfenstein
wolfsp.x86 $*

2.  Save this file to whatever name you want (runwolf? startwolf? whatever...) and make it executable.

3.  su to root (for some reason the following command doesn't work with sudo, you get permission denied)

4.  As root, execute 'echo "wolfsp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'

5.  Exit root and as your normal user, execute the script created above, the game should start, have smooth sound, and not hang on exit.

---

### Post by vinnie1 on 2010-01-14
Hi

Thanks for this post, works perfectly. :KS

---

### Post by ViperScull on 2010-01-14
what version of RTCW ET are you talking about?

I am using 2.60b and :

the executable file is et.x86 and not wolfsp.x86
the directory of enemy territory is /usr/share/games/enemy-territory and not /usr/local/games/wolfenstein

---

### Post by vinnie1 on 2010-01-14
Hi

I am just playing rtcw,

version 1.4 GOTY

---

### Post by NRDNick on 2010-06-20
For Wolf:ET all you need to do is open the et-sdl-sound script and change the value of sdl_audiodriver:"pulse" save it and you should be good to go.

---

