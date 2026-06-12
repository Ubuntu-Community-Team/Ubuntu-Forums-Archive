---
title: "Chromium sound"
date: 2005-10-21
forum: Gaming &amp; Leisure
---

### Post by jtopping on 2005-10-21
I have sound running in all of my current applications simutaneously, except for chromium....

For GAIM/System Sounds I use ESD, natively
For firefox flash, I use "aoss firefox" as flash uses OSS
for frozen bubble, i installed libsdldebian-alsa to force sdl to use ALSA
I also set gstreamer-properties to ALSA

for whatever reason, chromium is forcing itself to try and find the /dev/dsp device, which I believe to be the old OSS mixer device...i tried using aoss chromium, but I get nothing but static....is there a way to force it to use ESD or even an ALSA sink?

---

