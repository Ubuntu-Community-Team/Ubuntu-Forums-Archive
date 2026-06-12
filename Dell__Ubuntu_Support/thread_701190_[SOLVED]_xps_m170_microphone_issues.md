---
title: "[SOLVED] xps m170 microphone issues"
date: 2008-02-19
forum: Dell  Ubuntu Support
---

### Post by oni5115 on 2008-02-19
I can't seem to get my microphone working properly for recording in Ubuntu 7.10, on my XPS m170.  When I go into System > Preferences > Sound   I get the following when I test sound capture.

> Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

Using the Gnome Volume Control (v2.20.1) if I have the microphone under "playback" set to max, and under "switches" I have checked Microphone Capture and Mic Boost (+20dB), I can hear myself talking in my headset/speakers, however it does not seem to record anything at all.

I haven't been able to get a microphone working in Linux yet (on 3 different computers).  I always seem to have this issue.  Any way to fix it?

It's an Intel ICH6 with STAC9750,51 also control device.  (The default sound card.)



Solution:  I managed to get it working by selecting Capture in the audio settings and making sure it was un muted.... knew it had to be something simple.

---

