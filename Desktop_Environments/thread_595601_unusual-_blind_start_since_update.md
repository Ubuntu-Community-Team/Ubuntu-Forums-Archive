---
title: "unusual- blind start since update"
date: 2007-10-28
forum: Desktop Environments
---

### Post by Anacranom on 2007-10-28
OK, i turn on the pc, get to the grub menu, allow the default to Ubuntu, then i get  a monitor messatge "mode not supported" can hear the "ubuntu drums" that the log-in screen is up but cannot see it. I blindly log-in, and enter password, then all comes up and all is right with the world of Linux,, but that log-in is bothering me? Cant see anything but the Monitor's built-in error and have to blind-ly log--in?

---

### Post by markusf21 on 2007-10-29
Try this:
```
gksu gedit /etc/usplash.conf 
```
and make sure it's not trying to use a resolution you monitor can't handle

---

