---
title: "External mic with Ubuntu 9.10 on a Studio XPS 1340"
date: 2009-10-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Technoviking on 2009-10-29
I found a solution to getting an external microphone working on my Dell Studio XPS 1340 laptop with Ubuntu 9.10. First I needed to install the linux-backports-modules-alsa-karmic-generic package.

```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```
Then you should cold boot/shutdown your laptop and restart.

I just had to switch the Mic Jack setting in *alsamixer* from Line In to Mic In.

The first time an external mic has worked on this laptop with Pulse.

T-V

---

