---
title: "ZSNES crashes loading save state on 10.10"
date: 2011-01-06
forum: Gaming &amp; Leisure
---

### Post by ryanchang on 2011-01-06
Hello,

I was in the middle of Chrono Trigger, saved state, and it crashed. I reloaded ZSNES and tried to load the state and it crashed again. I can see right in the corner before it crashes that it loads the state. Here is the output from terminal:

> Starting Mouse detection.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
ao_alsa ERROR: Unrecognized channel name "&#65533; B&#65533;&#65533;t&#65533;&#65533;
<&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;                                           &#65533;
        &#65533;|&#65533;R&#65533;+1&#65533;&#65533;&#65533;&#65533;Í&#65533;&" in channel matrix "&#65533; B&#65533;&#65533;t&#65533;&#65533;
<&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;                                              &#65533;
        &#65533;|&#65533;R&#65533;+1&#65533;&#65533;&#65533;&#65533;Í&#65533;&"
ao_alsa WARNING: Input channel matrix invalid; ignoring.

Audio Opened.
Driver: Advanced Linux Sound Architecture (ALSA) output
Channels: 2
Rate: 44100

ZSNES could not find any joysticks.
Segmentation fault


I scoured some other forums and the solutions suggested are to manually edit the save paths, but this does not help. I still get a seg fault. Please help!! I got so far!

Ryan

---

