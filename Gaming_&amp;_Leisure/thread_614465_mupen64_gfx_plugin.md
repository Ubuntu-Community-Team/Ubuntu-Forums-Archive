---
title: "mupen64 gfx plugin"
date: 2007-11-16
forum: Gaming &amp; Leisure
---

### Post by Metallion on 2007-11-16
Hi

I've just downloaded mupen64 and I'm having a hard time getting it to work. The main problem is that it's not giving me a choise of which graphics plugin to use. The only one that shows up in the list at the config screen is TR64 OpenGL v0.7.8 and it's not working for me.

This is the contents of my plugins dir:
```

blight_input.so  Glide64.so      mupen64_audio.so           RiceVideo6.1.0.ini
dummyaudio.so    glN64-0.4.1.so  mupen64_hle_rsp_azimer.so  ricevideo.so
Glide64.ini      glN64.so        mupen64_input.so           tr64gl.so
Glide64.ini~     jttl_audio.so   mupen64_soft_gfx.s

```

Obviously the other gfx plugins are there but they are not showing up in the configuration window. Has anyone encountered this problem before? My google searches have had no results so far.

---

### Post by Metallion on 2007-11-17
bump :(

---

### Post by tab0u on 2007-11-18
I have exactly the same problem!I have try everything out with no results(change plugin permissions etc)

EDIT:Man im really fast!!:P

The problem is that the rest of the plugins depends on libstdc++5 and we(i think) have libstdc++6.If you try to run mupen64 with "mupen64" in terminal and try to change video plugin,you can see in terminal the error messages!
So i have downgrade to libstdc++5 and works!


PS.Sorry for my bad english.

---

### Post by Sockerdrickan on 2007-11-18
There's a new Mupen64 coming

---

