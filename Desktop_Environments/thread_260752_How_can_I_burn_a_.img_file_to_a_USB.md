---
title: "How can I burn a .img file to a USB?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by broadfootp on 2006-09-19
I'm trying to burn a .img file (which are meant for floppies) to a USB drive, so I can use it to boot with.

How can I do that with Ubuntu?

---

### Post by fakie_flip on 2007-04-15
Have you tried dd? If your usb device is /dev/sda, then you can do this.

dd if=file.img of=/dev/sda

---

