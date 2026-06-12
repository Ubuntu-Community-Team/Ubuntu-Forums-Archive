---
title: "Dualbooting Kubuntu/Ubuntu and no grub entry for Kubuntu"
date: 2009-04-14
forum: General Help
---

### Post by JECHO on 2009-04-14
I just resized my 500GB Ubuntu partition to dual boot with Kubuntu and once I installed Kubuntu on the free HD space and restarted, there was no entry in Grub... I checked GParted and the filesystem is there but I think it just wasnt added to the grub menu.list does anyone know how to add Kubuntu to the menu.list file? I know how to edit that file I just am not sure what the UUID of my kubuntu partition is. how do i find it?

Thanks guys.

---

### Post by askreet on 2009-04-14
You need to know the UUID of the location of the /boot directory, which I think in Kubuntu is the same partition as /.

Do this in a terminal:
```
ls -l /dev/disk/by-uuid/
```

You should see something like:
```
laptop% ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-04-14 05:17 5973158c-b58c-496a-af16-9355ab5b2286 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-04-14 05:17 731651fc-b3e5-4260-a7ed-6784fc668450 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-04-14 05:17 8a237b1d-0ba2-43b2-b813-b906d7723edf -> ../../sda4
lrwxrwxrwx 1 root root 10 2009-04-14 05:17 B4EE1D64EE1D1FE2 -> ../../sda1

```

Theres your linux-name-to-uuid mapping.

Hope this helps!

---

