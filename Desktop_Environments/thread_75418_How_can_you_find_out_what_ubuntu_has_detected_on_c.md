---
title: "How can you find out what ubuntu has detected on com1?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by greengrass on 2005-10-13
where do you look to see if ubuntu has configured the com ports?

---

### Post by drogoh on 2005-10-13
Serial (COM) ports aren't detected.  The only way you'll know something is connected is if you can connect to the device.  I don't know if it exists in Linux, but over at the FreeBSD camp I picked up a little tidbit for connecting to serial devices and it's 'cu -l /dev/cuaaX' (where cuaaX is FreeBSD's device name, it'd be different in Linux and NOT cuaaX if 'cu' exists in a package)

---

