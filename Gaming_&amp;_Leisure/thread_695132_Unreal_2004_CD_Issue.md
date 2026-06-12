---
title: "Unreal 2004 CD Issue"
date: 2008-02-12
forum: Gaming &amp; Leisure
---

### Post by Crafty Kisses on 2008-02-12
When I'm trying to install it I insert disc 1, then it tells me to insert disc 2, when I do that and try to eject my Drive it says "The Drive is busy" any ideas? Thanks!

---

### Post by Crafty Kisses on 2008-02-12
This is the exact error:

```
codename@codename-desktop:~$ sudo eject /media/cdrom0
```

```
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/media/cdrom0' failed
```

---

### Post by FrozenFox on 2008-02-12
Try moving the installer sh file to your desktop first, then running it from there. 

If you still get the errors, in the console try forcing the unmount with umount instead of eject perhaps, sudo umount /media/cdrom0  (umount, not unmount).

---

### Post by nebu on 2008-02-13
does unreal tournament have a different linux edition or does it install from the same cd that works in windows????


i cant seem to find the installer in the windows cd

---

### Post by FrozenFox on 2008-02-13
[http://www.liflg.org/?catid=6](http://www.liflg.org/?catid=6)

UT2004 comes with one on the cd (except for on the anthropology edition), but I imagine youre also talking about ut99, which does not. Loki has, however, made an installer for native linux.

---

