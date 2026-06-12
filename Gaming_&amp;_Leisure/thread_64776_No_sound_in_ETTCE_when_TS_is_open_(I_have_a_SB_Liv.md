---
title: "No sound in ET/TC:E when TS is open (I have a SB Live! card)"
date: 2005-09-12
forum: Gaming &amp; Leisure
---

### Post by Russ[] on 2005-09-12
I read that you need hardware mixing to do this, and my card has it. What's the deal?

```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```

they give me permission denied's =(

---

### Post by J.K.Makowka on 2005-09-13
You have to do that with sudo or in a root window

---

