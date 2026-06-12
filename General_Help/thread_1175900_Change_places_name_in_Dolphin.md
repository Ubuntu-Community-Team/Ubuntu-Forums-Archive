---
title: "Change places name in Dolphin"
date: 2009-06-01
forum: General Help
---

### Post by Graham1 on 2009-06-01
Hi

Is it possible to change the partition name (i.e Volumn (ext3) ) within Dolphin?

:)

---

### Post by Graham1 on 2009-06-02
Bump ;).

:)

---

### Post by michy99 on 2009-06-02
I'm not a Dolphin user, but I think what you need to do is to give the volume a label using tune2fs.```
tune2fs -F <LABEL> /dev/sda1
```Where <LABEL> is the label you want, and /dev/sda1 should be changed to the desired partion. I'm not sure if the partition should be unmounted first, but it is probably a good idea. You may have to reboot to see the difference.

---

