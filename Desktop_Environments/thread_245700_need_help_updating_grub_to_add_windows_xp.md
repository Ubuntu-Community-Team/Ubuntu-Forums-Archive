---
title: "need help updating grub to add windows xp"
date: 2006-08-28
forum: Desktop Environments
---

### Post by rkakkar on 2006-08-28
I installed ubuntu on /dev/hda1. I then attached another hard disk containing windows xp. The hard disk is detected as /dev/hdc. How can I add windows xp to grub? The "C:" drive is on /dev/hdc1. Currently my menu.lst looks like:

```

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot


```

---

### Post by anaconda on 2006-08-28
# Windows
title  Windows
map (hd0,0) (hd2,0)
map (hd2,0) (hd0,0)
rootnoverify (hd2,0)
savedefault
makeactive
chainloader +1

should work.. (hope it does.. )

---

### Post by rkakkar on 2006-08-29
hi .. it didn't work.. it said that it could not find the device or something like that.. i think the problem is with hd2. Btw, why do we have those two map statements? what is the purpose? :).. also, when it boots up, grub gives me 2 seconds to press escape to go into the menu and if i am not quick enough it starts booting ubuntu (without going into the grub menu). How can I change this so that everytime i boot up, i should see the grub menu directly?

---

