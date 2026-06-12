---
title: "Alsa sound problems"
date: 2006-06-21
forum: Desktop Environments
---

### Post by gosh on 2006-06-21
Hi,

I have a problem with ALSA.
I have no sound.
When I run gstreamer-properties I get the error:

```
- using device default
- using device default
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsrc'
- using device default
- using device default
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
gstreamer-properties-Message: Error running pipeline 'Autodetect': Could not establish connection to sound server [esdsink.c(252): gst_esdsink_open (): /actual-sink:
can't open connection to esound server]
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open resource for writing. [gstalsasink.c(833): gst_alsasink_open (): /pipeline1/alsasink3:
Playback open error: No such file or directory]

```

Even if i try the other possibilites, no luck:confused:

---

### Post by gosh on 2006-06-22
It seems to be a kernel problem.
I read a lot of post of people having trouble after upgrading to 2.6.15-25.

I rebooted into 2.6.15-23 and now I have sound again.
I'll check if really everything is ok.

---

### Post by Kuraboy on 2006-06-25
[QUOTE=gosh]It seems to be a kernel problem.
I read a lot of post of people having trouble after upgrading to 2.6.15-25.

I rebooted into 2.6.15-23 and now I have sound again.
I'll check if really everything is ok.[/QUOTE]

I have the same problem, when I log into .15-23 there is sound, but not in .15-25

---

