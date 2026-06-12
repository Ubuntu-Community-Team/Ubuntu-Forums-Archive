---
title: "Vendetta Online + Pulse Audio"
date: 2008-06-14
forum: Gaming &amp; Leisure
---

### Post by MechWarrior001 on 2008-06-14
I tried to install the Creative X-Fi sound driver for Linux, and now my VO automatically switches to OSS and I hear no sound. Worse, I can't find the Creative X-Fi files & delete them.

But I was messing around in System>Preferences>Sound and this is what I Have:

Nvidia CK8S - IEC958: Shows "Testing..." Dialog but no testing sound.

Nvidia CK8s through OSS = "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application."

PulseAudio = Testing Dialog with Testing sound.

So, I was thinking, If PA was the only (correctly) working SD, is it possible to run VO using PulseAudio Sound Server?

---

### Post by Fred_E _krugar on 2008-06-14
Hail {S} MechWarrior,


I have to say that I have had nothing but problems with Pulse Audio so What I have found to work is just shut the Pulse Audio server off in the processes then restart your games and music.


Btw I used to play Mech2,3,4 Mercs. They dont make em like that anymore.

---

### Post by MechWarrior001 on 2008-06-15
What do you mean by the "{S}"?

---

