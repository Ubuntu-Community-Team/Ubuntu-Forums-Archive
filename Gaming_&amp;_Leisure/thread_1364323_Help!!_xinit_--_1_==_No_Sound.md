---
title: "Help!! xinit -- :1 == No Sound"
date: 2009-12-25
forum: Gaming &amp; Leisure
---

### Post by Dark Aspect on 2009-12-25
Hi,

I have a very big problem, since my computer is outdated I normally execute newer/stressful games via a minimal desktop with xinit and kill gnome. However simple xwindows under Ubuntu 9.10 doesn't seem to have sound and I am unable to play newer/stressful games at a decent speed. When I start another xorg and launch a sound application this is the message that I get:

```
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: Permission denied
```

Yes I realize I could solve this problem by buying a rather cheap dual core processor but I would rather continue to take the cheap way out. My five year old single core CPU still has some life to it :)

---

### Post by Perfect Storm on 2009-12-26
Read somewhere that upgrading to the latest Alsa will solve a lot of problems like this. 

There's a PPA for it: [http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html](http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html)

NOTE!!! USE IT ON YOUR OWN RISK.

---

