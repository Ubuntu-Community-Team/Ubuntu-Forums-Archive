---
title: "/ is readonly with unknown option"
date: 2009-05-04
forum: General Help
---

### Post by endfx on 2009-05-04
A bad mistake lead me to edit the / line in my /etc/fstab file to read:
/dev/sda1   /   ext3  acl,defaults,eerrors=remount-ro 0    1

Notice the "eerrors..." option. Now when I reboot, / is mounted read-only. I've try to remount it with:

mount -o remount -w /
mount -o remount,rw /

And I always get:
mount: / not mounted already, or bad option
And dmesg adds:

EXT3-fs: Unrecognized mount option "eerrors=remount-ro" or missing value

I'm sure this could easily be fixed by getting a boot CD, mounting and fixing fstab, but I wanted to know if there is any other ways of fixing it without a rescue cd.

I hope a typo in fstab can't paralyze a system.

Any ideas?

---

### Post by taurus on 2009-05-04
You need to boot into recovery mode from GRUB menu and drop into root shell.  Then, modify your /etc/fstab.

Or boot from Ubuntu LiveCD.  Mount the partition where / is and edit /etc/fstab.

---

### Post by endfx on 2009-05-04
Booting into recovery from grub still results in it being read-only. The only option is to use a boot cd?

---

### Post by taurus on 2009-05-04
Yes, use the LiveCD then.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab
```

---

