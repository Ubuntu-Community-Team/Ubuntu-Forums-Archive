---
title: "Adding mount option to a usb device has rendered it unmountable"
date: 2009-02-01
forum: Desktop Environments
---

### Post by QwUo173Hy on 2009-02-01
I connected my usb storage device (Blackberry with 2.0gb memory card) to my 8.04 installation. It mounted fine but was read only.

I can't reproduce what happened next to give a better description but I right clicked the device icon and found a dialog for adding volume specific mount options. I added "-w" to try to make it read/writeable.

Now I can't mount the device at all. On connection, Gnome says "Cannot mount volume.Invalid mount option when attempting to mount the volume." and I can't access the same dialog to undo the change I made.

I can mount through the command line and perform my actions there but obviously I want my default behaviour back.

I hope someone can help because as it stands I don't even have a good enough description to file a bug report yet.

---

### Post by QwUo173Hy on 2009-02-03
A reboot solved the problem.

---

