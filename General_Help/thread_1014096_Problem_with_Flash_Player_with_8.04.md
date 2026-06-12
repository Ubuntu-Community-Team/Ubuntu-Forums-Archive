---
title: "Problem with Flash Player with 8.04"
date: 2008-12-17
forum: General Help
---

### Post by metallicarox2009 on 2008-12-17
So i'm running Ubuntu 8.04, and i've downloaded and installed Flash Player 10, but i'm still not able to visit flash sites in Firefox. Youtube, VW.com, Google Street View, Etc.  What am i doing wrong?

---

### Post by Ayuthia on 2008-12-17
Just to get some of the simple questions out of the way, have you restarted firefox?

Also, can you check:
```
ls -l /usr/lib/mozilla/plugins
```and make sure that libflashplaer.so is there.

Did you uninstall the flashplayer-nonfree before you installed the new version of flash or is that what you installed?  I am not for sure what version Hardy is using for flash.

---

### Post by utnubuuser on 2008-12-17
I've also read that if you install the flash-nonfree plugin from synaptic rather than any other source...

There was something about un-installing any other instances of flash, than installing the nonfree flash plugin.

---

