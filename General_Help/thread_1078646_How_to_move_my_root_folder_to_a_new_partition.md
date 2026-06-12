---
title: "How to move my root folder to a new partition?"
date: 2009-02-23
forum: General Help
---

### Post by Diabolis on 2009-02-23
Which is the correct way to move my root folder(/dev/sda1) to a new partition(/dev/sda2)?

Would this be ok:
```
sudo mv /dev/sda1 /dev/sda2
```

and then edit grub menu?

---

### Post by kellemes on 2009-02-23
> **Diabolis said:**
> Which is the correct way to move my root folder(/dev/sda1) to a new partition(/dev/sda2)?

Would this be ok:
```
sudo mv /dev/sda1 /dev/sda2
```

and then edit grub menu?

Boot from liveCD (whatever brand). Mount your two partitions, copy all from your /-partition to the new one.

Now, change /-partition in /etc/fstab and edit /boot/grub/menu.lst to boot from your new partition.

Edit: always assume things go wrong.. so backup stuff.

---

