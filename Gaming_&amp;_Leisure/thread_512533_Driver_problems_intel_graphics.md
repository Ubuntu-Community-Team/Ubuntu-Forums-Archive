---
title: "Driver problems: intel graphics"
date: 2007-07-29
forum: Gaming &amp; Leisure
---

### Post by CC_machine on 2007-07-29
What driver should i use for my laptop? I've been trying to play sauerbraten and cube on it, and the performance is really abysmal compared to what i get on windows. I did a quick benchmark (looking at the whole of metl3 map with occluders off):

Windows XP: 40 FPS
Ubuntu 7.04: 14 FPS
This is at the same resolution and conditions, this sucks :(

i have the intel driver installed from synaptic (i upgraded from the i810), and it's rendering with Mesa. Specs:

Dell Inspiron 6400 model
1GB DDR2-533 ram
120gb drive (22gb for ubuntu partition)
1.73ghz intel core 2 duo
intel GMA 950

So, where can i find a proper driver? =[ 
Thanks in advance!

---

### Post by darksidedude on 2007-07-29
does your card have suport for 3d render?

tell me the output of this plz
```
  glxinfo | grep "direct rendering"  
```

---

