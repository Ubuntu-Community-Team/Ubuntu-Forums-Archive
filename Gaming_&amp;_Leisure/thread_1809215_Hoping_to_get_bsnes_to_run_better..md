---
title: "Hoping to get bsnes to run better."
date: 2011-07-21
forum: Gaming &amp; Leisure
---

### Post by Sahasrahla on 2011-07-21
I just installed bsnes v080 and it's running at about 35 fps. I would like to believe that my computer is good enough and that it's just some settings but here's my stats.
natty narwhal
intel pentium 4 2.26ghz
512mb
nvidia gforce fx 5500 256mb
ensoniq es1371 sound card

when I type free -m I get 146 free and 317 buffer/cache.

Is it that my comp isn't good enough for bsnes or that I have some settings and tinkering to do?

---

### Post by disturbedite on 2011-07-21
Seems good enough to me.
The system requirements from the bsnes page state this:
Intel Core 2 Duo or AMD Phenom processor
Video card that supports Direct3D 9.0 or OpenGL 2.0
Linux port: hardware-accelerated video driver with OpenGL or X-Video support

---

### Post by DoktorSeven on 2011-07-21
Yeah, bsnes is a beast, you need a pretty good system to run it.  Try zsnes or snes9x-gtk, it'll run better though they're not as "perfect" of a SNES emulator as bsnes is.

---

### Post by byuu on 2011-07-22
> **Sahasrahla said:**
> Is it that my comp isn't good enough for bsnes or that I have some settings and tinkering to do?

Should be fast enough, but just barely.

Edit bsnes/Makefile, and change "profile := accuracy" to "profile := performance"
Now run "make clean && make && sudo make install" to rebuild it all.

Now open bsnes, go to Settings->Advanced. Make sure either OpenGL or X-Video is used for your video renderer. The audio driver doesn't matter, just find the one that you like best. You must restart the emulator after changing the video settings for it to take effect.

Failing that, your last option is to utilize profile-guided optimizations. Build with the two profile generation lines, then run a couple games with it, then make clean and build with the profile usage line. This part is tricky to do, but will give you another 10-15% speedup.

---

### Post by Sahasrahla on 2011-07-22
> **byuu said:**
> Should be fast enough, but just barely.

Edit bsnes/Makefile, and change "profile := accuracy" to "profile := performance"
Now run "make clean && make && sudo make install" to rebuild it all.

Now open bsnes, go to Settings->Advanced. Make sure either OpenGL or X-Video is used for your video renderer. The audio driver doesn't matter, just find the one that you like best. You must restart the emulator after changing the video settings for it to take effect.

Failing that, your last option is to utilize profile-guided optimizations. Build with the two profile generation lines, then run a couple games with it, then make clean and build with the profile usage line. This part is tricky to do, but will give you another 10-15% speedup.

I was able to change to the performance build and switch to x-vid which got me to 55-60 fps. I would like to do the profile-guided optimizations but it's much too above my understanding. Thank you for replying, It really shows how much you care about your emulator that you'll help people with tech issues like this in a somewhat personal manner.

---

