---
title: "Festival &amp; ALSA"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Benn on 2005-11-28
Hi. Today I installed festival speech synth but it says that cannot find /dev/dsp

My audio apps works well, wich /dev/* uses in Breezy ?

Bye

---

### Post by cwaldbieser on 2005-11-28
[QUOTE=Benn]Hi. Today I installed festival speech synth but it says that cannot find /dev/dsp

My audio apps works well, wich /dev/* uses in Breezy ?

Bye[/QUOTE]
Try:
```

$ ls /dev | grep dsp

```
It might be something like dsp1 or dsp2 if you have multiple sound cards.

---

