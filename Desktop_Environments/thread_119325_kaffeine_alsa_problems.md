---
title: "kaffeine alsa problems"
date: 2006-01-19
forum: Desktop Environments
---

### Post by cirpo on 2006-01-19
hi, my computer has two sound cards, onboard and pci.
I decided to use the pci one because the onboard is a hda intel (can't have a full control).To set the pci card as default i put asound.conf in /etc
```
pcm.!default {
type hw
card 1
}

ctl.!default {
type hw
card 1
}

```
Everything works fine except kaffeine, no sound at all.The only way to make it works is to put the jack in the onboard card.I think it's a xine problem, because it has rhe same problem.
how can i fix it?

---

