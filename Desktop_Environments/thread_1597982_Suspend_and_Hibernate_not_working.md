---
title: "Suspend and Hibernate not working"
date: 2010-10-15
forum: Desktop Environments
---

### Post by GuitarG20 on 2010-10-15
Hi all,
My suspend and hibernate buttons are not working. When I try to return from a suspend, I do not get a kernel panic, but nothing loads onto the screen. (It is a wubi install if that helps)

does anyone else have this problem/what is a fix?

---

### Post by inobe on 2010-10-16
the only fix is an actual hard drive install, suspend to disk and hibernate are the only downsides to wubi.

these are wubi limitations [http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29#Limitations](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29#Limitations)

---

### Post by GuitarG20 on 2010-10-16
very interesting. especially since I used to be able to suspend on a wubi'd Dell Inspiron laptop (made in 2002) with 9.04 and 9.10.

---

### Post by inobe on 2010-10-16
never been able to but it may just work on certain hardware.

---

### Post by bcbc on 2010-10-16
Suspend should work on wubi. Hibernate does not (actually that's nothing to do with wubi it's to do with the fact that wubi uses a swap file - to hibernate you need a swap partition).

---

### Post by inobe on 2010-10-16
> **bcbc said:**
> Suspend should work on wubi. Hibernate does not (actually that's nothing to do with wubi it's to do with the fact that wubi uses a swap file - to hibernate you need a swap partition).

well you got my attention, whats the procedure ?

thanks

---

### Post by bcbc on 2010-10-16
> **inobe said:**
> well you got my attention, whats the procedure ?

thanks
Create a swap partition. Change the /etc/fstab. Update /etc/initramfs-tools/conf.d/resume with the UUID and run update-initramfs -u.

That's it.

(The reason noone does it is because the whole point of wubi is that you don't need to partition :) )

---

### Post by inobe on 2010-10-16
> **bcbc said:**
> Create a swap partition. Change the /etc/fstab. Update /etc/initramfs-tools/conf.d/resume with the UUID and run update-initramfs -u.

That's it.

(The reason noone does it is because the whole point of wubi is that you don't need to partition :) )

awesome :)

---

