---
title: "mount removable devices readonly"
date: 2009-04-03
forum: General Help
---

### Post by jonolte on 2009-04-03
Hello!

For security reasons I have to mount removable devices like usb memory sticks readonly by default! (xubuntu intrepid ibex)

How to manage it?

Is there a guru out there who can give some advice!

---

### Post by TyrantWave on 2009-04-03
In terminal, do:

```
mount -o ro /media/disk
```

(Where disk is the name of the USB drive, this may change).

I wouldn't know how to do it by default, but you could set up an alias in the terminal for USB devices.

(Ie, alias usb="mound -o ro /media/disk" would mean whenever you type usb in the terminal it mounts the USB in read only)

---

### Post by jonolte on 2009-04-04
> **TyrantWave said:**
> In terminal, do:

```
mount -o ro /media/disk
```

(Where disk is the name of the USB drive, this may change).

I wouldn't know how to do it by default, but you could set up an alias in the terminal for USB devices.

(Ie, alias usb="mound -o ro /media/disk" would mean whenever you type usb in the terminal it mounts the USB in read only)

Ok! This is not my problem!
Removable USB media are automounted! The automount process should mount read only!

Any advice

---

