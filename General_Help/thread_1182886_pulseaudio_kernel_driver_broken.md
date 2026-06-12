---
title: "pulseaudio: kernel driver broken?"
date: 2009-06-09
forum: General Help
---

### Post by whoop on 2009-06-09
What's this? In messages
```

Jun  9 19:47:42 ASUSP5B pulseaudio[4302]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Jun  9 19:47:42 ASUSP5B pulseaudio[4302]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Jun  9 19:47:42 ASUSP5B pulseaudio[4302]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.

```
Audio is working, might be softer than usual. 
82801H (ICH8 Family) HD Audio Controller, HDA Intel Sound Card (onboard)
How to fix?

---

### Post by whoop on 2009-06-09
Looks like it's complaining about hw:1. 
What command can I use the figure out which device is linked to hw:1 ?

---

### Post by whoop on 2009-06-10
I'll answer my own question
```

aplay -l
arecord -l

```

---

