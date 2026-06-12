---
title: "Mouse stopped working"
date: 2008-08-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by undoIT on 2008-08-11
I have a Dell Latitude D830 with Ubuntu Hardy 8.04 64-bit. I left the laptop in sleep for a couple of days. After opening the lid this morning, the mouse is no longer working. Neither the tracking stick nor the touchpad are working. I have rebooted twice. The external mouse is working. The built-in mouse works in the BIOS.

This is the first significant problem I have had with Ubuntu since installing Hardy Heron right after it was released. Any suggestions?

---

### Post by mrynit on 2008-08-12
you could look in /etc/X11/xorg.conf to see if there are any input devices.

boot into an older kernel.

---

### Post by undoIT on 2008-08-12
Strange. This morning I cold booted with the external USB mouse plugged in. Then the touchpad and tracking stick started working again. I shut down and rebooted. Still working.

I had cold booted two times before (without the external mouse plugged in) and the built-in mouses refused to work. I guess it was one of those flukes.

---

### Post by mrynit on 2008-08-13
i guess you could mark the thread as solved :-|

---

