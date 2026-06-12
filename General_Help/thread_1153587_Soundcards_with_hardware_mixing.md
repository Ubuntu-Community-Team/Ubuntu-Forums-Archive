---
title: "Soundcards with hardware mixing?"
date: 2009-05-08
forum: General Help
---

### Post by mrowth on 2009-05-08
Here's my /proc/asound/pcm:
00-00: VIA 8237 : VIA 8237 : playback 4 : capture 1
00-01: VIA 8237 : VIA 8237 : playback 1 : capture 1

I take this to mean my onboard sound has 4 (hardware) channels available... or 5, with subdevice 1? What's subdevice 1, anyway? It doesn't seem to make a difference which I use, only I can't make (say) Amarok and JACK both use hw:0,1 (but hw:0,0 is ok).

**What's the output for some other soundcards?** While I still want to get a better soundcard (ideally suited for some cheap goofing-off with recording/MIDI/synth apps), I don't want to run into all the scary problems people are having with apps and sound servers blocking each other out! (Right now I can run (say:) Amarok 1.4 + JACK + Atari emu + Commodore emu + Flash + Zblast + Audacity at the same time without thinking too much about whether I'm going to make them use /dev/dsp or plughw:0 or hw:0,0 or default or Phonon (which in turn seems to go through x-phonon:0,0, plughw:0,0, /dev/audio, /dev/dsp, x-phonon:0,1, plughw:0,1, /dev/adsp, xine->pulse, xine->ESD...). Only rarely do I have to switch an app to another interface/device/plugin/? to make sound work for it.)

---

### Post by mrowth on 2009-05-09
Bump...

Could I at least get some random **cat /proc/asound/pcm** outputs 
from random kind visitors 
with random soundcards, be they cheap & nasty or pro gear
+ statements as to what works/doesn't work?

---

