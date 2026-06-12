---
title: "Kmix with 24/96 Sound Card"
date: 2007-12-16
forum: Desktop Environments
---

### Post by BobvanderPoel on 2007-12-16
I have an Maudio Audiophile 24/96 sound card. Works fine (well, apart from the fact that the Midi outputs freeze, so I don't use them). But, the audio part works okay. I'm using KDE, so that pretty much means that I have the kmix applet running in the taskbar.

Problem is that the 24/96 has 2 channels for the left/right audio volume. In the gnome mixer they are labeled ADC and ADC1. In kmix they are both ADC. 

In gnome one can link the 2 channels together. In kmix, it doesn't seem to be possible. Does anyone know if it is possible to link or tie the ADC and ADC1 together so that the kmix volume slider controls both channels? The best I can get is EITHER left or right.

---

### Post by BobvanderPoel on 2008-01-26
BUMP ... anyone with ideas on this ... or a pointer to another forum to try?

---

### Post by ldrn on 2008-05-22
You kept at it for a few months judging by your bump and I ran across this while trying something similar...

It sounds like you need a soft volume control to control both with Alsa; you can then set this to the "Master Channel" in kmix.  I found instructions here:
[http://alsa.opensrc.org/index.php/How_to_use_softvol_to_control_the_master_volume]("http://alsa.opensrc.org/index.php/How_to_use_softvol_to_control_the_master_volume")

---

