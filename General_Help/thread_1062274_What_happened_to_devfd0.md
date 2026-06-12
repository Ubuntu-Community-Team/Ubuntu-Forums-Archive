---
title: "What happened to /dev/fd0"
date: 2009-02-06
forum: General Help
---

### Post by fm1234 on 2009-02-06
Hi,
I wanted to copy some old floppies but the floppy is not automatically mounted and actually there is no /dev/fd0. There is a link /dev/fd to /proc/self/fd.

What can I do to read the floppies?

---

### Post by Tim Sharitt on 2009-02-06
Open a terminal and enter
```
sudo modprobe floppy
```

If you would like the floppy module loaded on boot add:
```
floppy
```
to /etc/modules

---

### Post by fm1234 on 2009-02-06
Thanks, I guess fd are too old devices by now :-)

Hmm, Thread Tools has no option to close the thread...

---

