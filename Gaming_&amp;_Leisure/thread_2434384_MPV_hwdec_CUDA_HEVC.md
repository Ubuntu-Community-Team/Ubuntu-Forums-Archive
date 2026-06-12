---
title: "MPV hwdec CUDA HEVC"
date: 2020-01-04
forum: Gaming &amp; Leisure
---

### Post by themedserv on 2020-01-04
I have some trouble reading some HEVC mkv with cuda Hwdec and MPV

I have GTX 1060 and some video works perfectly HW Decoding with MPV and some other (I would say 50/50 chance) start with a big green screen and bug after a minute of playback.
Thing is, these broken playback works flawlessly without HWDEC options (on CPU)

I have the 440 NVidia driver installed from the run file on their website.

Wondering if I am doing something wrong or it is the nvidia implementation that is buggy?

Maybe thinking of getting a RX 560 instead. Would that be better option?

Running LUbuntu LTS 18.04

---

### Post by themedserv on 2020-01-04
I just updated MPV with PPA, and use nvdec instead all working now :D

---

