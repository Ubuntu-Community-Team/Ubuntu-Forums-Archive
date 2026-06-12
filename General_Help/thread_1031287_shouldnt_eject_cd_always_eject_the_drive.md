---
title: "shouldnt eject cd always eject the drive?"
date: 2009-01-05
forum: General Help
---

### Post by tgpraveen on 2009-01-05
when i have a cd/dvd in my drive and i select the eject cd option. then t works properly.

but if there is no cd in the drive then i get a error stating that nothing is mounted or something like that.

shouldnt it always eject the drive. coz i dont want to use the hardware eject button on my dvd rom as it is old and doesnt work.

so is it like this for me or for everyone?
always why is it like this? any logical reason?

---

### Post by ajcham on 2009-01-05
The GNOME dev team are on it apparently (it is an issue with gnome-mount): [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/203574](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/203574)

Until they get it fixed, you can use the eject command from a terminal (or create a desktop launcher or menu item to do same):
```
eject /dev/cdrom
```
If you have more than one drive, you may need to use /dev/cdrom1, or similar, depending on which you are using.

---

### Post by Slim Odds on 2009-01-05
> **ajcham said:**
> Until they get it fixed, you can use the eject command from a terminal (or create a desktop launcher or menu item to do same):
```
eject /dev/cdrom
```If you have more than one drive, you may need to use /dev/cdrom1, or similar, depending on which you are using.

You could also make a quick launch button on the panel that does this.

---

### Post by tgpraveen on 2009-01-05
thx a lot.really helpful.

---

