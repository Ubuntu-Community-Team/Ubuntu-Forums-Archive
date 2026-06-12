---
title: "No Sound 9.04"
date: 2009-05-07
forum: General Help
---

### Post by triunenature on 2009-05-07
Ok, so here's the gist, When i login to my account, i hear the login sound, so i know sound works in basic.  When i try to play a sound file, it doesn't work.  When i go to a website to play sound it doesn't work.  When i play a .ogv file (music/vidoe file) it doesn't work (error message on the ogv file).

Any ideas?

Found sound card:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Found sound modules using :
```
find /lib/modules/`uname -r` | grep snd
```

Found device:
```

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Gateway 2000 Device 4040
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 501c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```

And last but not least all my other relevent sound info:

[HTML]http://www.alsa-project.org/db/?f=941e2fbefb8e4d0ddd204c169fe7099d82ff7de8[/HTML]

---

### Post by triunenature on 2009-05-07
*bump*

New info, i opened audacity, and generated a sign wave.  It played through my speakers fine. 
**ADDED - I converted an mp3 over to an audacity file, and it played.  So the issue isn't hardware or alsa, it must be something else not allowing my mp3's or internet to play sound, or my linux moves to play 


And i checked, i cant get my mp3s to play through banshee or move player, or my ogv files (get errors with both).  And still can't play stuff online

---

### Post by Acapulco on 2009-05-07
I also have some sound issues, although I can play fine any type of media file except for sound in webpages/flash.

Totem player, VLC, etc work just fine.

Ubuntu 9.04 here, on an Inspiron 1420 with Intel audio and using the HDA Alsa driver.

---

