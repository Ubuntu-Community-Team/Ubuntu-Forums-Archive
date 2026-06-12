---
title: "Update manager crashing"
date: 2006-07-19
forum: Desktop Environments
---

### Post by AvvY on 2006-07-19
I just put together a makeshift computer from the following parts:

1ghz P3 s370
MSI m-atx
2x256mb 184ram
10gb maxtor hdd
dvd-rom
cd-rw

I've got 6.06LTS installed - and it's damn nice. But I've found the updater crashing the whole system. On a fresh install there were around 130 packages to update at around 180m. I decided I didn't need a few of them - specifically OO.o. I reduced it down to around 108 packages at ~98m.

So it went ahead and downloaded 107 packages and froze during 108. I rebooted, same issue. Tried again. It kept locking up. I'm now just running memtest to see if it is memory related - I got all these parts of the side of the road so it could very well be hardware related. But curious to know if this is in fact Ubuntu. I noticed Ubuntu froze a few other times randomly, but otherwise seems to be fine.

---

### Post by Perfect Storm on 2006-07-19
Try do it the update through synaptic package manager instead, it worked for me. (experienced the same thing as you)

---

### Post by AvvY on 2006-07-19
Tried as you suggested, worked a treat. I had to fix a stack of broken packages, then upgraded fine. Cheers!

Oh, and just a note it also all crashed when trying to do this via terminal previous to trying Synaptic.

---

