---
title: "UQM (amd46) in Breezy"
date: 2005-11-08
forum: Gaming &amp; Leisure
---

### Post by vitku on 2005-11-08
I was wondering if anyone would know how to make uqm (ur-quan masters) work in breezy/amd64

The game installs fine through apt-get, but when I try to run it it says

```
The Ur-Quan Masters v0.3 (compiled Aug 30 2005 17:43:56)
This software comes with ABSOLUTELY NO WARRANTY;
for details see the included 'COPYING' file.

Saved games are kept in /home/vitku/.uqm/save/.
Initializing SDL (pure).
SDL driver used: x11
SDL initialized.
Initializing Screen.
Set the resolution to: 640x480x32
Initializing SDL audio subsystem.
SDL audio subsystem initialized.
Initializing MixSDL mixer.
MixSDL using driver 'SDL_audio'
MixSDL Mixer initialized.
    opened dsp at 44100 Hz 16 bit stereo, 4096 samples audio buffer
Initializing sound decoders.
Sound decoders initialized.
0 joysticks were found.
        'lbm/title.ani' -- 19 bytes
/usr/games/uqm: line 3: 14810 Segmentation fault      "/usr/lib/games/uqm/uqm" "--contentdir=/usr/share/games/uqm/content" "$@"
``` 

It would be great to have some moments of nostalgia with the game.

---

### Post by Yagisan on 2005-11-09
IIRC it is also broken on Debian amd64. You should file a bug at [http://launchpad.net](http://launchpad.net)

---

