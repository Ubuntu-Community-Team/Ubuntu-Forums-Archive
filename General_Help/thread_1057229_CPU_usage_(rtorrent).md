---
title: "CPU usage (rtorrent)"
date: 2009-02-01
forum: General Help
---

### Post by guilhermecardoso on 2009-02-01
Good evening.

I'm having a problem with my CPU usage. When i run htop i get 100% usage of CPU, and that was strange. So, i run top and i get this output:
> Tasks: 105 total,   1 running, 104 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.7%us,  1.0%sy,  0.0%ni,  2.9%id, 91.7%wa,  0.9%hi,  1.7%si,  0.0%st
Mem:    474684k total,   468776k used,     5908k free,     7808k buffers
Swap:   488824k total,    42096k used,   446728k free,   378308k cached

The iowait is very very high (91.7%). So, i use ps aux to find processes with stat "D" (i think that's waitig for some type of comunication with HD). I found just one with stat D, it was rtorrent.
I am running rtorrent through a screen (to stay always running). 
I typed pmap to rtorrent. Rtorrent is using 64MB.
My CPU is a Intel(R) Celeron(R) CPU 220 @ 1.20GHz.

What you advice me to do? Is ram used by rtorrent normal? And about iowait, what can i do?

Thanks

---

### Post by guilhermecardoso on 2009-02-01
By the way, i'm using rtorrent with xmlprc (because rtgui).
I'm just with 3 torrents on rtorrent and the owait stills 97%.

---

