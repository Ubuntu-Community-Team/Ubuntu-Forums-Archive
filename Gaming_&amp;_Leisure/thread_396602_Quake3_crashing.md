---
title: "Quake3 crashing"
date: 2007-03-29
forum: Gaming &amp; Leisure
---

### Post by t341 on 2007-03-29
I've seen this question asked a number of times in these forums 
but I haven't seen it answered yet.
I tried using a terminal command to help with Quake3 sound,
"quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
which makes the game unstable and crash prone.
Does anyone know how to remove the effects of using this
command and revert my sound setup to how it was before
running this command?

---

### Post by bo_jo on 2007-03-29
> **t341 said:**
> I've seen this question asked a number of times in these forums 
but I haven't seen it answered yet.
I tried using a terminal command to help with Quake3 sound,
"quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
which makes the game unstable and crash prone.
Does anyone know how to remove the effects of using this
command and revert my sound setup to how it was before
running this command?


try
"quake3.x86  0  0  disable" > /proc/asound/card0/pcm0p/oss

---

