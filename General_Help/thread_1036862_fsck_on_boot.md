---
title: "fsck on boot"
date: 2009-01-11
forum: General Help
---

### Post by frankdn on 2009-01-11
Is there a way to "dump" tune2fs's current settings?  I haven't seen a boot-time fsck in quite a while (it's been well over a month, now) and I'm wondering if something's misconfigured.  I'd like to look at tune2fs's current settings before I go mucking about.

Thanks!

---

### Post by Taxman415a on 2009-01-11
What information do you need? It should all be accessible with the ```
sudo tune2fs -l [filesystem]
``` option. See man tune2fs for more. It is quite difficult to follow, but it does all seem to be in there.

---

### Post by frankdn on 2009-01-11
-l is the answer, thanks!

---

