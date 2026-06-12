---
title: "[SOLVED] OpenAl NO SOUND"
date: 2008-05-10
forum: Gaming &amp; Leisure
---

### Post by dhysk on 2008-05-10
No games will play sound. i've tried various openalrc conifgs
it currently looks like this:

(define devices '(alsa native arts esd null))
(define alsa-device "default")
(define speaker-num 2)

any suggestions.

---

### Post by dhysk on 2008-05-10
ok i feal like a moron.  See, my onboard sound cards front speaker channel died so i put in a really old card in the pci slot so i can hear the main sound.  Ubuntu automatically finds the card that works, somehow, but apparently Ubuntu doesn't make this the 'default' device.  Anyway long story short i just put in

(define lin-dsp-path "/dev/dsp2")

the openalrc now looks like

(define devices '(alsa native arts esd null))
(define lin-dsp-path "/dev/dsp2")
(define speaker-num 2)
(define sampling-rate 44100)

---

