---
title: "[SOLVED] OSS audio fails in Cedega"
date: 2007-09-18
forum: Gaming &amp; Leisure
---

### Post by stinkinrich88 on 2007-09-18
Hello

I'm trying to play GTA san andreas in cedega, I've done it before with my last install of Ubuntu (i'm pretty sure, if not it was fedora) anyway, I try to load the game and it gives me a sound card error.

When I run the cedega tests everything passes except OSS audio. Any ideas what might be wrong?

thank you!

---

### Post by misfitpierce on 2007-09-18
I believe on ATI cards OSS always fails and has no effect on games. That's my remembering... I also read that it's common for ATI card's and is not to be worried about. You have an ATI card?

---

### Post by stinkinrich88 on 2007-09-18
ohh, good point, last time I managed to get it working I was on a MSI motherboard with built in audio, now I'm on an Intel motherboard with inbuild audio. I use NVidia graphics

---

### Post by stinkinrich88 on 2007-09-19
Hey Rich, here's the solution:

type 

```
winecfg
```

into your terminal, then click the audio tab, tick "OSS Driver" and select "Emulation" from the hardware acceleration drop down.

easy! (probably a restart too)

---

