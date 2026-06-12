---
title: "What triggers the disk check upon boot?"
date: 2009-05-13
forum: General Help
---

### Post by GammaPoint on 2009-05-13
As I was waiting for Ubuntu to boot up this morning due to a disk check, I became curious as to what the trigger was for this to happen. Does it happen every say, X, startups, or is there another trigger? Just curious. Thanks!

---

### Post by michy99 on 2009-05-13
By default, it checks every 30th mount. You can change it with tune2fs. A nice how-to is 

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by GammaPoint on 2009-05-13
Thanks for the answer!

---

### Post by exutable on 2009-05-13
It's approximately every 30 boots and it basically just checks for inconsistencies and bad sectors.  Linux doesn't fragment like windows because it actually checks how much space there is before it writes.

---

