---
title: "Neverwinter nights, no sound"
date: 2014-03-26
forum: Gaming &amp; Leisure
---

### Post by Lancro on 2014-03-26
Ive searched in the forums, in google, and everything fails, in nwn, if I take out the ./lib:, the following message appears...

./nwmain: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

Ive Installed libsdl1.2debian libsdl-sound1.2 libsdl-mixer1.2 libsdl-net1.2 libsdl-image1.2 libstdc++5 and libx11-dev, Ive tried with the option export SDL_AUDIODRIVERS=pulse, but nothing, no sound at all, can anyone help me?.

Ubuntu 13.10 64 bits.

Thanks.

---

### Post by Nikobelia on 2014-03-29
Have you got Pavucontrol installed? If so a good first step is to look for Neverwinter Nights in the Playback tab and check which audio device its output is going to. You can just play some audio that works from Firefox or your media collection or something and check the playback device matches it lists for the game, that will rule out a lot of problems.

---

