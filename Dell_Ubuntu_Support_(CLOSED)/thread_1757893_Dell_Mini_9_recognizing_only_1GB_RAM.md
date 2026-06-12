---
title: "Dell Mini 9 recognizing only 1GB RAM"
date: 2011-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kakotako on 2011-05-14
I've had Dell Mini 9 for 2+ years. It still has Ubuntu 8.04 on it. I bought it new with 2GB RAM. However, it never recognized more than 1GB (I've been lazy to check why until now). I vaguely remember reading some post at the time that there was a limit of 1GB in Ubuntu for some reason.

When I execute:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1000        869        130          0         30        448
-/+ buffers/cache:        391        609
Swap:            0          0          0

```

Under the assumption that I really have 2GB installed which I will physically check later, what could be the reason Ubuntu is unable to see it all?

---

### Post by kakotako on 2011-05-14
Silly me, the answer is right here:[URL="http://ubuntuforums.org/showthread.php?t=1001898"]

http://ubuntuforums.org/showthread.php?t=1001898[/URL]

---

### Post by toufiqueimam on 2011-05-14
check that u may shared other one gb ram as graphics share from bios.

---

