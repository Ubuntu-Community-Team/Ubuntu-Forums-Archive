---
title: "udev rules for 2 sound cards"
date: 2006-07-14
forum: Desktop Environments
---

### Post by hannes_ on 2006-07-14
hey m8s, 

got the following problem.

I got 2 sound cards on my system, and udev sends them to /dev/dsp0 and /dev/dsp1

actually this is the way it SHOULD work, but it doesent.

From boot to boot udev switches snd card 0 to dsp1 and snd card 1 to dsp0, next boot its card 0 to dsp0 .....

so how can i tell udev that the onboard snd card should be dev/dsp0 and the snd snd card dev/dsp1.

on breezy this worked like a charm for me.

Any help on this would be great

$ cat /proc/asound/cards
 0 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
                      C-Media PCI CMI8738-MC6 (model 55) at 0xd400, irq 209
 1 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1985 at 0xf7fff800, irq 217

---

