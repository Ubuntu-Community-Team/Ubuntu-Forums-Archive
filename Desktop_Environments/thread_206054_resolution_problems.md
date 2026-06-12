---
title: "resolution problems"
date: 2006-06-29
forum: Desktop Environments
---

### Post by Lster on 2006-06-29
I haven't yet been able to fix my screen resolution for my laptop. It has a native 1280x800 resolution but ubuntu only allows resolutions up to 1024x768. I have an ATI mobility radeon 1400 with 256MB of GDDR2 RAM which should be fine at 3d (plays Far Cry on Windows) but screensavers are really jerky on Ubuntu.

---

### Post by harishg on 2006-06-29
Did you install the fglrx driver for radeon.? 

Backup your xorg.conf file and give it a try.You might get 1280*800 if the driver works.

---

### Post by Lster on 2006-06-29
Sry to be a N00B, but how would I do that?

---

### Post by harishg on 2006-06-29
you can get it using synaptic.First step would be finding out if your graphic card is supported.In a terminal type lpsci and look for the ati radeon name.

Open synaptic and do a search for flgrx and check in the message if your graphics card is supported.If not dont bother as it wont work.

If you are not sure just post the configuration file obtained after typing lpsci and I can tell if your card is supported.

---

