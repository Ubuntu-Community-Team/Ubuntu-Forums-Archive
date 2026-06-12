---
title: "How to remove kxmame...?"
date: 2008-03-04
forum: Gaming &amp; Leisure
---

### Post by Moonfrost on 2008-03-04
Hi, I installed kxmame for sdlmame from svn on the net (not the repos) and I wanted to remove it because I found another better frontend. apt-get install remove doesn't work since I didn't download it from the repos...anybody know how can I remove it from my system? and without actually living any files?

---

### Post by FranMichaels on 2008-03-04
Try

sudo apt-get remove kxmame

or 

Load Synaptic, search for kxmame, then right click on it and choose remove completely.

:KS

---

### Post by Moonfrost on 2008-03-04
> **FranMichaels said:**
> Try

sudo apt-get remove kxmame

or 

Load Synaptic, search for kxmame, then right click on it and choose remove completely.

:KS

I tried both things before but it didn't work since I didn't install it through Synaptic and it's not even the same version that's available in Synaptic at all...the one there is outdated and doesn't support sdlmame, only x-mame and x-mamex...

---

### Post by ryanhaigh on 2008-03-04
see if there is an uninstall script in the directory from which you installed it.

---

