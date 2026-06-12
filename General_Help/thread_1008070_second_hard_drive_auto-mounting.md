---
title: "second hard drive auto-mounting?"
date: 2008-12-11
forum: General Help
---

### Post by oknos on 2008-12-11
Hi there, my problem is that i have to mount my second hard drive each time i start ubuntu.
Although i don't face a serious problem, i'd like to know if there is a way for it to be mounted automaticaly in each new session.

thanks in advance.

---

### Post by Archmage on 2008-12-11
If you put it in the /etc/fstab it should be automounted.

---

### Post by davidbilla on 2008-12-11
Try adding something like the following in /etc/fstab.
```

/dev/sdb1	/media/my_disk	ext3	defaults	0	2
```

This is only an example. Substitute 'sdb1' and 'my_disk' with your device name and mount point.

In fact, you will find some lines starting with 'UUID' in /etc/fstab. Find the UUID of your hard drive and substitute in the place of '/dev/sdb1'. This will help even if you added more hard drives or changed the order (like with another HD, sdb may become sdc and the new one could become sdb).

---

### Post by oknos on 2008-12-11
thanks a lot! 
problem solved! it was quite simple actually...:p

---

### Post by davidbilla on 2008-12-16
Hi,

Mark this thread as 'SOLVED' from the 'Thread Tools' option. It'll help others too.

---

