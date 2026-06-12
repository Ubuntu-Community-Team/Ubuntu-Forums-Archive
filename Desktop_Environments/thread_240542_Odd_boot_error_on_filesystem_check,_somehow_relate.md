---
title: "Odd boot error on filesystem check, somehow related to pcmcia"
date: 2006-08-21
forum: Desktop Environments
---

### Post by sumadartson on 2006-08-21
This morning I was greeted with the following lovely error message when my system decided to do a filesystem check:

```
udevd-event[3635]:wait_for_sysfs: waiting for '/sys/devices/platform/i82365.0/bus' failed
```

I managed to escape the filesystem check by hitting ctrl-c and continuing booting.

Anyone any idea what might cause this problem?

(According to an old dapper drake development post this apparently a pcmcia related issue, but there was just a question in that post, no usable answer...?)

---

