---
title: "cdrecord - operation not permitted."
date: 2005-11-09
forum: Desktop Environments
---

### Post by Jad on 2005-11-09
> /usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted

any idea how to fix this permission problem ?

---

### Post by Kyral on 2005-11-09
Its trying to run with Root power, which you aren't invoking. I don't know if cdrecord needs root priv, but you can get around it by invoking it with sudo.

---

### Post by Jad on 2005-11-09
yes I know, I'm trying to avoid running k3b with sudo

---

### Post by Kyral on 2005-11-09
I thought this problem was fixed in Breezy....

Fire up your Users and Groups admin and add yourself to the recording group or whatever it is (I can't check right now b/c I'm away from my computer)

I'd also file a bug in Launchpad ([www.launchpad.net](www.launchpad.net))

---

