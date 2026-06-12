---
title: "e2fsck and mounted fs"
date: 2005-06-15
forum: Desktop Environments
---

### Post by mirtux on 2005-06-15
Hi,
  i need to run e2fsck on a mounted ext3 filesystem (/dev/hda1): it says me 
 ```

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

``` 
How to run it without mounting that partition considering that hda1 in the / partition?

Regards,
MC

---

### Post by angkor on 2005-06-15
Use any liveCD.

---

### Post by GTvulse on 2005-06-15
Unless you need to perform a very special task (say, rebuild and optimize the directory tree), there is no need to use a live cd: ```
sudo shutdown -Fr now
``` will repair the filesystem safely.

---

### Post by mirtux on 2005-06-16
Thanks!

Regards,
MC

---

