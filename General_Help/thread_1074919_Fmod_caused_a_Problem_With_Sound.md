---
title: "Fmod caused a Problem With Sound"
date: 2009-02-19
forum: General Help
---

### Post by jcoaster2008 on 2009-02-19
I am running Ubuntu 8.10, and recently installed Racer. It said I needed to install the Fmod Api library for sound, so I downloaded the latest Fmod from the site and installed it. Racer never worked, and now no sound is working at all.

When I go to the sound preferences and click "Test" on any of the sound playback devices, it comes up with:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

I cannot figure out if this is due to Fmod being installed (because it occured right after I installed it) or if it is just a general sound problem. Does anyone know how I can fix this? My first step would be to unintall Fmod, but I don't know how.

---

### Post by aseptilena on 2011-04-16
Hello,

I found the solving for fmod error in racer...

edit the audio section in "racer.ini"

look at the bold letters, that's the edited things.....

audio
{
  ; Turn off enable (0) in case of sound problems
  ; All platforms use FMOD ([www.fmod.org](www.fmod.org))
  enable=**1**
  ; Set mastervolume; 0 is silent, 255 is maximum volume
  mastervolume=255
  ; Output; for Windows, use 'dsound', 'winmm', 'asio', 'openal', 'wasapi' (Vista) or leave empty
  ; to autodetect. For Linux, use 'oss', 'alsa', 'esd' or also
  ; leave empty. For Mac, use 'mac' (or empty).
  ; Try empty for starters. In case of trouble, try 'nosound' or enable=0 above.
  type=**oss**
  ; Output quality
  frequency=44100
  ; Bits per sample; 16-bits sounds much better and the mixer
  ; is optimized for 16-bit anyway.
  bits=16

---

