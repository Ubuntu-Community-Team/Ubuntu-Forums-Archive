---
title: "No Sound on Dell Inspiron, Ubuntu 8.10"
date: 2009-04-11
forum: General Help
---

### Post by VrmpX on 2009-04-11
Hello,

 Since the last update, I've got no sound at all. I've already ruled out Hardware problems since Vista sound works perfectly. As far as I've read, it is an issue with the updated kernel?

 I've tried several solutions already posted but none seem to work for me. I've upgraded Alsa to 1.0.9 but still no sound. I've installed and uninstalled Alsa drivers, pulseaudio and nothing. I get no sound at all.

 In preferences/sound whenever I select autodetect and click test an error pops-up saying : "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused" and when I pick Alsa, this error happens: "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback."

 I've also tried restarting alsa using the terminal. When thats done, I end up without sound. When I click on the sound panel, the following error appears: "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

 I'm using Ubuntu 8.10 with a Dell inspiron 1520. The audio device is "Inter Corporation 82801H (ICH8 Family)". And I'm sure that it works with ALSA since I works perfectly when booting from a Ubuntu live CD.

Any help is appreciated, thanks for the time.

---

