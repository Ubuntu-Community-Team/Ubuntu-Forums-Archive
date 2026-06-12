---
title: "CRW thumbnails"
date: 2008-10-25
forum: Desktop Environments
---

### Post by BA20 on 2008-10-25
Hi,

I'm looking for the program that makes thumbnails of CRW-files (RAW pictures) in Nautilus 2.20.0. I'm using Ubuntu 7.10, Gutsy Gibbon.

I normally use UFRAW to convert my CRW-pictures to JPG, but the colors differ from the colors in the thumbnails that are sometimes better.

thanks,

BA20

---

### Post by BA20 on 2008-10-27
Doesn't anyone have an idea? or a clue which could help me to find the solution?

thank you,

---

### Post by cepal on 2009-01-02
Yeah I would be graceful for such a hint as well :-(


UPDATE:
=====
 I just did "apt-cache search crw" and similar and found some candidates, which I installed and after a reboot (system froze, I am suspicious about an older keyboard/mouse/CRT switch which is using PS/2 and it is not as durable as USB) I can see the thumbnails in nautilus as well as the pictures themselves in any image viewing program (F-Spot is in my case the default one)...

Looking to my /var/log/dpkg I installed these packages:
exifprobe
2.0.1-1build1
libgtkimageview0
gimp-ufraw
ufraw
libc6

Not sure which one helped, either exifprobe or ufraw, the others were just dependant and gimp-ufraw was suggestion. They are all from the "universe" pool.

HEUREKA :-D

---

