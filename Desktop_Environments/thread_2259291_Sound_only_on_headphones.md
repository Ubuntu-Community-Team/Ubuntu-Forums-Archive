---
title: "Sound only on headphones"
date: 2015-01-03
forum: Desktop Environments
---

### Post by anieruddha on 2015-01-03
Hi,

There is no sound via Speaker. But when I connect headset, I can hear sound.

OS : Ubuntu 14.04
Dell 7537 laptop

Thanks
Aniruddha

---

### Post by ajgreeny on 2015-01-03
Run alsamixer in terminal and check that the levels of outputs for speakers and headphones, which are separate in volume output, are set to what you want.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

Pulseaudio-volume-control which you get to from the volume icon in your panel, choosing Sound-Settings can also set these levels, but you may have to install **pavucontrol** package to get that on your system.

---

