---
title: "Sound Blaster X-fi"
date: 2008-07-25
forum: Desktop Environments
---

### Post by ebursley on 2008-07-25
I have a Dell Precision 690 that came with a Sound Blaster X-fi card. I've looked in many different places for driver modules for this card, but the only thing I can find are dated articles related to ALSA team having the card, but no working drivers.
Does anyone have this sound card working?  I'm not opposed to compiling a custom driver into my kernel as I'm already running a custom kernel to support PAE.
I'm running Ubuntu 8.04.

---

### Post by evets25 on 2008-07-25
X-fi cards are not suported. Creative has yet to release proper drivers for it. They have released a "driver" that is alpha-quality, but they don't support even basic features other than basic playback (sometimes). So in other words, no, your sound card is not really supported. Sorry. :(

---

### Post by notlim_hardy on 2008-07-25
It does work as long as you install OSS instead of ALSA. Both are work in progress, but OSS will give you basic playback functionality, no recording though.

---

