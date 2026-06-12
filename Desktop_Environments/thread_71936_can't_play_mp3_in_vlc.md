---
title: "can't play mp3 in vlc"
date: 2005-10-04
forum: Desktop Environments
---

### Post by loell on 2005-10-04
hi,

   i attempted opening mp3 file in vlc player but it has no sound output, but my audio is fine, i mean i can hear music in audio cd. i tried opening it in command line and the output is

[00000263] mpeg_audio packetizer: MPGA channels:2 samplerate:44100 bitrate:128
[00000286] mpeg_audio decoder: MPGA channels:2 samplerate:44100 bitrate:128
[00000288] oss audio output error: cannot open audio device (/dev/dsp)
[00000288] main audio output error: couldn't find a filter for the conversion
[00000288] main audio output error: couldn't set an output pipeline

 i also tried installing  vlc-alsa hoping it would make a difference, but it still does not work.

so may i ask what could have cause this problem?

---

### Post by Perfect Storm on 2005-10-04
Try to uninstall vlc-alsa and install vlc-esd instead. Next you have to go to preference in vlc, choose advance and pick Audio to be "Esound".

---

### Post by loell on 2005-10-04
Thank you....

  now i can play mp3:p :p :p

---

### Post by Perfect Storm on 2005-10-04
My pleasure ^^

---

