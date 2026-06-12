---
title: "[SOLVED] Not allowed to do anything!"
date: 2009-01-03
forum: General Help
---

### Post by Java Geek on 2009-01-03
I try to mount my flash disk and this message keeps pestering me

A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal")

If anybody can aide me with this issue, it would be amazing. THANKS

---

### Post by cariboo on 2009-01-03
How are you trying to mount your usb device? Are you just plugging it in and let it automatically? Can you mount it from the command Line?

Jim

---

### Post by Java Geek on 2009-01-04
I can mount it from the command line with sudo. However I just fixed it with sheer luck . I found an error message elsewhere on my system that told me to run sudo dpkg --configure -a. When I did and reooted my system, it fixed all my problems. Thanks for your help though

---

