---
title: "Restarting sound service?"
date: 2009-06-24
forum: General Help
---

### Post by kooldino on 2009-06-24
I have a Creative Labs X-Fi sound card.  Occasionally, the sound will freak out and play some annoying sound in a continuous loop.  I'd like to be able to restart the sound service or somehow fix this without a reboot.  Any ideas?

---

### Post by kooldino on 2009-06-24
11 hours later and it's still in this loop.

---

### Post by kooldino on 2009-06-24
So I just noticed that amarok was running in my tasktray area (but on pause).  I closed it, and the crazy high pitched loop went away.  My sanity is back.

---

### Post by KhaaL on 2009-09-05
a late response i know, but hopefully will help others with this problem in the future.

sound in kubuntu can be restarted with the following command:
sudo /etc/init.d/alsa-utils restart

---

### Post by kooldino on 2010-02-04
Thanks!

---

