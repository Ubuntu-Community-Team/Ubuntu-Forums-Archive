---
title: "No Audio through HDMI in Return To Castle Wolfenstein"
date: 2009-04-26
forum: Gaming &amp; Leisure
---

### Post by gdbutcher on 2009-04-26
Hi I'm not getting any sound at all in Return To Castle Wolfenstein. I'm using the HDMI Audio/Video on Radeon HD4850. Which works in everything else (firefox, flash, ETQW, Quake 4, Urban Terror, VLC, Myth Tv etc). I've had sound problems previously with RTCW which I fixed by adding this line:

```
echo "wolfsp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```

in /etc/rc.local

this doesn't work for me with HDMI.

Any suggestions anyone?

---

