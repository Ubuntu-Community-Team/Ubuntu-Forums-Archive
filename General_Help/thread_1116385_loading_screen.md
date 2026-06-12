---
title: "loading screen"
date: 2009-04-04
forum: General Help
---

### Post by bsta520 on 2009-04-04
when my loading screen is up i have to press and hold a key...any key ... for it to continue loading, otherwise it wont load... any ideas??  thanks

---

### Post by 3Miro on 2009-04-04
Try booting without the splash screen:

1. Backup grub menu list
2. Change the boot option to "nosplash"
3. Reboot

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_mybackup
sudo pico /boot/grub/menu.lst

```

Look for the place that looks like:
```

title           Ubuntu 8.10, kernel 2.6.27-11-generic
uuid            **********
kernel          /boot/vmlinuz-2.6.27-11-generic root=*** ro quiet splash
initrd          /boot/initrd.img-2.6.27-11-generic

```

and change it to:
```

kernel          /boot/vmlinuz-2.6.27-11-generic root=*** ro quiet nosplash

```

---

### Post by bsta520 on 2009-04-06
so you want me to delete the other things and just leave that one?

if thats what it is i tried and i couldnt get it to delete.

---

