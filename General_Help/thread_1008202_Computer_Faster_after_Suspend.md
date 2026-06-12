---
title: "Computer Faster after Suspend"
date: 2008-12-11
forum: General Help
---

### Post by ripps818 on 2008-12-11
I've just discovered the weirdest thing ever: my computer runs faster after I suspend my computer. 
Usually, when I play 720p+ h.264 video, it stutters and is impossible to play. But after I resume from a suspend, it plays perfectly.  
During a fresh reboot, decoding h.264 uses 100% cpu; after resuming from suspend, decoding uses 80%. 
What's going on here?

Just so you know, I'm using SMplayer with CoreAVC, but the performance advantage for most decoders is increased as well.
My hardware is Athlon XP 2500+, Nforce 2 chipset, ATI Radeon 9600 Pro (Open Source ATI: EXA=on, AGPMode=1).

If we can figure out what's going on here, then whatevers causing this increased performance can be applied at boot.

---

