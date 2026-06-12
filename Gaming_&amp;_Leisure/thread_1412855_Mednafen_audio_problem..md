---
title: "Mednafen audio problem."
date: 2010-02-21
forum: Gaming &amp; Leisure
---

### Post by Bu7753x on 2010-02-21
```
 Initializing sound...
  Using "ALSA" audio driver with device "default":ALSA Error: snd_pcm_open(&alsa_pcm, id ? id : "hw:0", SND_PCM_STREAM_PLAYBACK, 0) Device or resource busy
Error opening a sound device.

```

What am I missing here/how would I fix this?

---

### Post by disturbedite on 2010-02-21
make sure no other application or service is using your sound card or is locked to your sound card (such as a hung application or service).

---

### Post by Spectre5 on 2010-06-22
I'm having the same problem as the OP.  I know that I DO have another application running with audio, but I WANT that.  How can I get audio to be heard from two programs at the same time (i.e. say I want to listen to music as well as the game music in mednafen).  How can I do this?

I've tried searching around and I've tried numerous suggestions, but none have worked so far.  Since pulseaudio seems to usually be the problem, I even tried uninstalling pulseaudio.

---

### Post by mocha on 2010-07-13
mednafen doesn't work with pulseaudio.  If you are not using pulseaudio then you need to setup alsa to use dmix to play sounds from more than one app at a time.  The Arch Linux wiki has a great information about how to set that up on the Alsa page.

---

### Post by Cresho on 2010-07-14
kubuntu works miracles with no pulseaudio

---

