---
title: "Rhythmbox settings?"
date: 2005-09-03
forum: Desktop Environments
---

### Post by veraction on 2005-09-03
(forgive me, I am noob & don't know what i'm doing)

Is there some configuration text file?

I want to check what sound device/system thing it uses. I was having issues with XMMS before & was able to fix it by switching the sound device/system thing from ESD to ALSA.

I now want to switch Rhythmbox to ALSA if possible.

---

### Post by cbudden on 2005-09-03
[QUOTE=veraction](forgive me, I am noob & don't know what i'm doing)

Is there some configuration text file?

I want to check what sound device/system thing it uses. I was having issues with XMMS before & was able to fix it by switching the sound device/system thing from ESD to ALSA.

I now want to switch Rhythmbox to ALSA if possible.[/QUOTE]
 Go into xmms, press ctrl-p, then change the output to alsa (i think)

---

### Post by veraction on 2005-09-03
yes.. that was easy. now I want to change to ALSA for rhythmbox

---

### Post by doclivingston on 2005-09-04
Rhythmbox uses the same settings as all GStreamer-based applications. Go to Preferences->Multimedia Systems Selector (or gstreamer-properties from a terminal) and change the audio sink.

---

### Post by veraction on 2005-09-04
ah ok, thx a bunch. now to figure out how to get ALSA to work (which I thought worked before ;))

---

