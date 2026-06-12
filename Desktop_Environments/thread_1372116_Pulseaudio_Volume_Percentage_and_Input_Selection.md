---
title: "Pulseaudio Volume Percentage and Input Selection"
date: 2010-01-04
forum: Desktop Environments
---

### Post by dimaspivak on 2010-01-04
Hi all,

After finding a fix for the crackling and popping noises that started after installing Karmic, I'm left with two minor Pulseaudio issues. First off, the "Output" percent acts in an unexpected way. In particular, on my system, all sound disappears promptly at 15% while it's nice and audible at 16%. Has anyone else encountered this and, if so, have you found a way to get back the normal "0% = zero sound" state yet?

Finally, I can only switch inputs (i.e. whether to have my Dell XPS M1330 use the built-in microphone or something plugged into the front connector) using alsamixer. The strange thing here is that "Sound Preferences" gives two options for "Connector" (Microphone 1 and Microphone 2), but neither turns off the built-in mic and turns on the front connector. Any thoughts?

Sincerely,
   Dima

---

### Post by dimaspivak on 2010-01-05
... bump... :)

---

### Post by Vaphell on 2010-01-05
well, pulseaudio has its share of problems

which alsamixer sliders move when you move system slider up and down? pa uses some weird algorithms of mixing few channels together to offer full scale of loudness (front, master, pcm moving together) but the results are often lacking. I chose pcm set at 80% to ignore volume slider and things were more predictable (in my case pcm > 80 causes hardware overdrive and really distorted sound so it doesn't make sense to move it higher).


[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/322909](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/322909)
> 1. sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
2. Go to the block titled "[Element PCM]" and change the line "volume = merge" to "volume = ignore"
3. Reboot (restarting PulseAudio isn't enough)

i guess you can choose different sliders to ignore system volume settings.

---

