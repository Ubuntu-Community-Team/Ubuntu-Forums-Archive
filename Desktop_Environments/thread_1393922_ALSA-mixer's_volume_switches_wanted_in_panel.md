---
title: "ALSA-mixer's volume switches wanted in panel"
date: 2010-01-29
forum: Desktop Environments
---

### Post by holydogtoffee on 2010-01-29
Hi,

I'm using Ubuntu 9.10 and I would fancy more than just the default volume switch in the panel.

How can I add more volume switches so that I can tune volume in different ALSA channels such as PCM, PCM Rear, PCM Side etc...

Yours,
holydogtoffee

---

### Post by holydogtoffee on 2010-01-30
Halp!

---

### Post by Zorael on 2010-01-30
Stop using PulseAudio, I think. It imposes its own one slider to rule them all.

---

### Post by holydogtoffee on 2010-01-30
I don't use Pulse!

I just want to know how can I add switches to GNOME desktop panel which control sound volume on different ALSA channels. (My headphones are on PCM, speakers on PCM Side)

The default switch controls PCM and it's stupid to keep alsamixer open all the time so that I can control PCM Side volume - I just want a quick handy slider on top of the panel.

---

### Post by Zorael on 2010-01-30
Ah, I see. Do prove me wrong, but I'm not sure that's possible without recompiling it. It seems hardcoded for pulse use.

Some snippets from [this launchpad bug report](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/400820);
> You say you purged Pulseaudio - but the new applet doesn't work without Pulseaudio anyway.
> g-v-c-applet is a pulseaudio client and should be able to autospawn the daemon on demand, like it does currently.
> While it was great that this symptom was solved, it doesn't fix the root of the problem (too much hard-coded dependence on Pulse).

In GNOME 2.26, the applet is called gnome-sound-properties (this is what System->Preferences->Sound points to). You get a nice GUI to configure gstreamer, media keys, and event sounds regardless of whether or not you have Pulse (this was also working in Karmic/GNOME 2.27 until recently).

One can use the gstreamer-properties command and build gnome-media from source (using the --enable-gstmix flag) to get a rough equivalent to that GUI, but n00bs aren't going to grok this (especially the ones that removed Pulse to fix their audio issues). The sensible thing would be to use the fancy Pulse volume features if Pulse is detected and fall back on the proven gstmixer if not.

A little off-topic: The same "use Pulse if there, fallback to gstreamer if not" should also apply to libcanberra, which is another needlessly broken package for those not using ALSA/Pulse. (When I built it with the gstreamer backend, my system sounds worked fine, even with OSS4.)

[This Google hit](http://n2.nabble.com/Re-Ubuntu-s-switch-to-pulseaudio-broke-accessibility-for-the-blind-td4073697.html#a4073697) describes a workaround consisting of installing custom packages from a ppa.

It's a shame such a solution is needed, but that's life for us not using the Default Setup.

---

