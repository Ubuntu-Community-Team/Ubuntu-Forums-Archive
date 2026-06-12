---
title: "what's the correct way to turn off usb disc drive?"
date: 2006-11-30
forum: Desktop Environments
---

### Post by mdurham on 2006-11-30
Hi Guys, can anyone tell me the correct way to turn off my usb drive please.
If I just turn off the power I get seven warning messages, one for each partition. If I 'eject' them I get a varying number of warnings "unable to eject media"
What's the right way of doing this?
Cheers, Mike

---

### Post by Johan! on 2006-11-30
Right click on the icon > unmount

When the icon disappears, the drive is unmounted. Then you can unplug the drive

Sorry. I tried it with my USB stick, it's eject, not unmount.

Your USB drives are probably mounted in /media/[volumename]
You can unmount them in a terminal:
```
sudo umount /media/volumename
```

---

### Post by mdurham on 2006-11-30
> **Johan! said:**
> Right click on the icon > unmount

When the icon disappears, the drive is unmounted. Then you can unplug the drive

Sorry. I tried it with my USB stick, it's eject, not unmount.

Your USB drives are probably mounted in /media/[volumename]
You can unmount them in a terminal:
```
sudo umount /media/volumename
```

Johan!, there is no 'unmount' when I right click the icon, only 'eject'
Unmounting seven partitions in the terminal is not my idea of fun!
Cheers Mike

---

