---
title: "ShedulingScans with Clamav?"
date: 2005-09-15
forum: Desktop Environments
---

### Post by er4z0r on 2005-09-15
Hi everyone,

This is my first post in this forum and I am quite new to Ubuntu and to Linux itself.

As mentioned above I would like to to use clamav to scan certain areas of my system in fixed intervalls of time (like with cron). How can I do that?

I have clamav and freshclam installed on a **Breezy Badger** (yes I do know this is forum is for hoary)

Does anybody have experience with clamav and samba on-access scanning?
There must be some kind of vfs-module for samba.

Thanks for your help

---

### Post by er4z0r on 2005-09-15
Well, thanks for your numerous posts. I think I figured it out now:

```
 0       */3     *       *       *       /usr/bin/clamdscan /shared/ 
```

Should scan the folder /shared/ every three hours each day.

---

