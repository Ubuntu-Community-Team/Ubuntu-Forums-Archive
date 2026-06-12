---
title: "Duplicate Tasks in Gnome's task bar"
date: 2012-07-31
forum: Desktop Environments
---

### Post by badinoff on 2012-07-31
Hello,

I am running 12.04 64-bit with an nVidia card. Proprietary driver is installed. I have two monitors, and running Gnome. My task bar shows all tasks twice (screenshot). Is there a way to fix that and have it show just one of each in the main monitor? Attaching XORG file just in case as well. 

Thanks!
BM

---

### Post by uglypewp on 2012-08-14
I have the same issue and it was after doing a dist upgrade to 12.04.  I am also using an nvidia card, nvidia 7600GT to be exact.  I tried switching between all the nvidia drivers listed in the additional drivers section with no luck.  Any chance you stumbled on a fix?

---

### Post by uglypewp on 2012-08-15
> **uglypewp said:**
> I have the same issue and it was after doing a dist upgrade to 12.04.  I am also using an nvidia card, nvidia 7600GT to be exact.  I tried switching between all the nvidia drivers listed in the additional drivers section with no luck.  Any chance you stumbled on a fix?

Looks like my problem stemmed from switching from twinview to separate xview in the nvidia-settings panel.  I was able to reset everything back by deleting ~.config/dconf/users then logging out and back in.

---

