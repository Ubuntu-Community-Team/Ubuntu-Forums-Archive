---
title: "UT2004 Sound Distortion (download link to hear it for yourself..)"
date: 2007-05-16
forum: Gaming &amp; Leisure
---

### Post by MikeReiner on 2007-05-16
[http://putstuff.putfile.com/80025/9220819](http://putstuff.putfile.com/80025/9220819)

just click next three time on that page to download it (it's only 1.5 megs)

All I did was install UT04 and put the openal.so file in the /System directory just to get the sound working..

sound hardware: NVidia CK804 (Alsa Mixer)
Realtek ALC850 rev 0 (OSS Mixer) 

Thats what the volume control says.. but I know it's an AC97.

Ubuntu Feisty 7.04.

---

### Post by Cappy on 2007-05-17
Try running it with
```
aoss ut2004
```

I don't know what else it would be unless you need to update openal or SDL.
I think they are these two:
```
sudo apt-get install libopenal0a libsdl1.2debian-alsa
```

---

### Post by MikeReiner on 2007-05-17
running with aoss doesn't work, and I have that package already.

---

### Post by shamanu on 2007-05-17
Hi! Try installing from Synaptic libopenalpp-cvs1 (the c++ version of openal, plus i think it's more recent), then backup openal.so form Ut/System folder, copy and rename libopenalpp-cvs into the UT/System folder. Try it now! (It worked for me!)

---

### Post by MikeReiner on 2007-05-18
> **shamanu said:**
> Hi! Try installing from Synaptic libopenalpp-cvs1 (the c++ version of openal, plus i think it's more recent), then backup openal.so form Ut/System folder, copy and rename libopenalpp-cvs into the UT/System folder. Try it now! (It worked for me!)

Thats what I had to do to get sound working in the first place.. I guess i'm just sorta unlucky here.

---

