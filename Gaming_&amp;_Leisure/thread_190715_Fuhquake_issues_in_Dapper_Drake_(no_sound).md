---
title: "Fuhquake issues in Dapper Drake (no sound)"
date: 2006-06-06
forum: Gaming &amp; Leisure
---

### Post by siriusnova on 2006-06-06
/dev/dsp: Broken pipe

i don't get any sound and that is the error message when i run fuhquake or any other quake client..

please help

---

### Post by ssmaxss on 2006-06-21
Use:
echo "fuhquake-gl.glx 0 0 direct" > /proc/asound/card0/pcm0p/oss
You may need to change card0 to cardX and/or pcm0p to pcmYp.
PS: Maybe setup official ubuntu quake server?

---

