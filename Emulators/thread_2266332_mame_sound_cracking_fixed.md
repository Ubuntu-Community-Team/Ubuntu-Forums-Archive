---
title: "mame sound cracking fixed"
date: 2015-02-21
forum: Emulators
---

### Post by hogrider on 2015-02-21
I just wanted to post this because after countless hours of searching and testing previous answers nothing worked.  All I had to do was change the samplerate in mame.ini from 48000 to 40000 and no more cracking sounds!  Simple fix, hopefully this will save someone else a lot of time.

## CORE SOUND OPTIONS
#
sound                     1
samplerate                40000
samples                   1
volume                    0

---

### Post by sffvba[e0rt on 2015-02-23
*Thread moved to **Emulators**.*

Good info, thanks.

---

### Post by MikeCyber on 2015-03-13
Thanks, adding to mame.ini bottom improves sound nicely.

---

