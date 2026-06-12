---
title: "Problems with sound at startup"
date: 2006-02-25
forum: Desktop Environments
---

### Post by BASICman on 2006-02-25
I've just set up Ubuntu 5.10 on my laptop (a Gateway 450SX4). The sound works fine, but the problem is that at startup the sound is so low that I can't hear it. I check the volume controls and my volume is at 100% and my PCI is at 85%. In fact, sound will not be at these levels until I move the PCI controls up and back, or until I try to load and play a sound in an audio player. Then everything works fine.

I think that this may be a problem with ALSA. Is there any way that I could ensure that the soundcard *knows* that its' volume is high at startup, as opposed to near muted?

---

### Post by bernardfrancois on 2006-02-27
Maybe you'll find more information in the man pages of *alsamixer* (I guess that's the name). (run **man alsamixer**)

---

