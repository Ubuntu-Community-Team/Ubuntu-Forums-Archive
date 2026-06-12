---
title: "Set up /dev/ttyUSB0 permission to '666' permanently"
date: 2009-01-23
forum: General Help
---

### Post by franziski on 2009-01-23
Was wondering how I can set up, permanently, 666 permission to "/dev/ttyUSB0".
Thanks in advance

---

### Post by Saubazi on 2009-01-23
can't say for sure now as I don't know what device you actually have as ttyUSB0 but a very strong bet is that you might want to do that in /etc/udev/rules.d and even perhaps in 40-basic-permission-rules or so... although for tty it would seem 666 anyway to begin with?

---

