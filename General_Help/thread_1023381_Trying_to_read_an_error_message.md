---
title: "Trying to read an error message"
date: 2008-12-27
forum: General Help
---

### Post by Trixilver on 2008-12-27
When I boot up 8.10 I'm getting an error message which is causing the whole system to simply hang for about five minutes - the problem is this message is scrolling so fast I can't read it.

Is there a way to read it from a log or maybe stop the messages during the boot so that I'm able to find out what's wrong with it?

---

### Post by spiderbatdad on 2008-12-27
```
dmesg > ~/Desktop/dmesg.txt
```This is a diagnostic message from the kernel.

---

