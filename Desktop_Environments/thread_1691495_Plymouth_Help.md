---
title: "Plymouth Help"
date: 2011-02-20
forum: Desktop Environments
---

### Post by inobe on 2011-02-20
hey guys, i got plymouth splash screen at the correct resolution, but i need to understand better about the FRAMEBUFFER=y comment in

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

is that suppose to create a config file, or does it open one?

when i run that, it's an empty file, can someone verify this?

i am following this from here [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

it's suppose to resolve the flashing cursor that i still see for 10 seconds before the splash.

---

### Post by Krytarik on 2011-02-20
Hi inobe,

you have to just put "FRAMEBUFFER=y" in that file, "splash", it is nothing else in there, it doesn't even exist by default.

After that run:
```
sudo update-initramfs -u
```

---

### Post by inobe on 2011-02-21
Krytarik thanks, running

```
sudo update-initramfs -u
```

again (second time) fixed the cursor issue.
the first time, i thought i was done, it was too fast, it put me back ready for another command within a second.

this time it showed my kernel, it was actually updating this time.

this is solved.

---

