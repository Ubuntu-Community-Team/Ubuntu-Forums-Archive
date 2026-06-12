---
title: "System performance"
date: 2005-06-17
forum: Desktop Environments
---

### Post by Delusional on 2005-06-17
after what seemed like a completely sucessful instal of kubuntu (sound and all) my sytem seems on a steady decline in performance.  after test driving several apps and konqueror my memory usage was almost 95% with no apps open. has anyone else had this problem it seem the progs are not being released from mem? maybe this is the way of things? not sure, new to linux at home? any help would be greatly appreciated.

---

### Post by Terracotta on 2005-06-17
Linux is built to use the max of memory, it doesn't clean the mem to access the data faster, here's a topic about it:
[http://forums.gentoo.org/viewtopic.php?t=175419](http://forums.gentoo.org/viewtopic.php?t=175419)
don't know if it solved your troubles.

---

### Post by Firetech on 2005-06-18
Type "free -m" in a console window (and press Enter).
The line saying "+/- buffers/cache" shows the "real" free memory.
Linux apparently allocates almost ALL available memory and (kind of) acts like a memory booster (Windows terms...) itself.

---

