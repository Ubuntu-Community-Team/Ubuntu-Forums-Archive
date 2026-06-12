---
title: "mount swap without using swapon"
date: 2009-04-27
forum: General Help
---

### Post by coreSOLO on 2009-04-27
I have a tricky question...

I am working on a mobile device where mkswap, swapon and swapoff commands are not available. What i did was to create a 64MB raw file using my lappy (linux), i formatted this raw file in "swap" format using "mkswap <myfile>" command (on my lappy) and everything was good. I now placed this file on my mobile device and trying to use this file as swap.

I tried "mount -t swap <myfile> none" but it does not work. Can someone please tell me how I can mount a swap file using "mount" command? "fstab" is not editable, so I need the solution as terminal "mount" command only...

---

### Post by coreSOLO on 2009-04-27
plz help someone...

---

