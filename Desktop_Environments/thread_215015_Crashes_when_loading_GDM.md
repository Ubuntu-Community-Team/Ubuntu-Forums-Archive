---
title: "Crashes when loading GDM"
date: 2006-07-13
forum: Desktop Environments
---

### Post by DeekoVB5 on 2006-07-13
I recently installed Ubuntu on my laptop.  It was working fine at first, but then it started freezing upon boot, as GDM is trying to load.  Normally, there is a blinking cursor, "_" at the top of the screen, and then GDM opens up.  Now, the cursor freezes and the system locks up.  If I boot in recovery mode, straight to the console, the system is working fine, I just can't get into GDM anymore.  I tried uninstalling/reinstalling it with apt-get to no avail.  Any ideas?

---

### Post by dseomn on 2006-07-13
You could try "dpkg-reconfigure xserver-xorg" in recovery mode which might fix problems with X configuration.

---

### Post by DeekoVB5 on 2006-07-13
Yup, I tried that.  It didn't fix it.

---

