---
title: "Problem Installing Omikron"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by Fowlwing on 2007-04-19
i started installing omikron, but then the loading screen dissapeared and i got the following in terminl

fowlwing@fowlwing-desktop:~$ winecfg
wine: creating configuration directory '/home/fowlwing/.wine'...
wine: '/home/fowlwing/.wine' created successfully.
fowlwing@fowlwing-desktop:~$ wine /media/cdrom/setup.exe
fowlwing@fowlwing-desktop:~$ X Error of failed request:  BadPixmap (invalid Pixmap parameter)
  Major opcode of failed request:  54 (X_FreePixmap)
  Resource id in failed request:  0x34001d6
  Serial number of failed request:  3330
  Current serial number in output stream:  3360


what is wrong?

---

### Post by justin whitaker on 2007-04-19
> **Fowlwing said:**
> i started installing omikron, but then the loading screen dissapeared and i got the following in terminl

fowlwing@fowlwing-desktop:~$ winecfg
wine: creating configuration directory '/home/fowlwing/.wine'...
wine: '/home/fowlwing/.wine' created successfully.
fowlwing@fowlwing-desktop:~$ wine /media/cdrom/setup.exe
fowlwing@fowlwing-desktop:~$ X Error of failed request:  BadPixmap (invalid Pixmap parameter)
  Major opcode of failed request:  54 (X_FreePixmap)
  Resource id in failed request:  0x34001d6
  Serial number of failed request:  3330
  Current serial number in output stream:  3360


what is wrong?

Looks like it is throwing an error reading the file from the CD. Try copying the contents from the disc to a folder on your hard drive, and use WINE to install from there.

---

### Post by kwr2k on 2007-05-07
Apparently this is a bug since version 0.9.34. Downgrading to 0.9.33 should solve this problem. 

See here:
[http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/fb9d70a2b5bbe6d1/1f41dbd21a129f5e](http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/fb9d70a2b5bbe6d1/1f41dbd21a129f5e)

---

