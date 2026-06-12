---
title: "Beeps on IBM T60 - Ubuntu 9.04 desktop"
date: 2009-05-16
forum: Desktop Environments
---

### Post by G0HXT on 2009-05-16
Hi clever people.  I have an IBM T60 that beeps when you hibernate.  I have stopped the beep when shutting down by editing the /etc/modprobe.d/blacklist.conf file and adding blacklist pcspkr but can't stop it on hibernation.

Any ideas? I'm running 9.04 desktop.

Thanks in advance - Andy

---

### Post by chakoshi on 2009-05-16
I'm not sure, but if you have black listed the pcspkr kernel module, the beep is not caused by linux kernel, I think you should take a look at your bios setup, there may be an option to enable/disable the beep

---

### Post by G0HXT on 2009-05-17
Thanks for your quick response chakoshi.  That sorted it, I looked everywhere except the obvious! :p

Andy

---

