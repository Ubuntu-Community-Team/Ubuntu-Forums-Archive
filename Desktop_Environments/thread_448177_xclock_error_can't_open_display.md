---
title: "xclock error can't open display"
date: 2007-05-18
forum: Desktop Environments
---

### Post by ak_saravanan on 2007-05-18
hi,

just installed ubuntu 7.04 feisty desktop model and trying to run xclock and getting this error

root@Abimanyu:~# xclock
Error: Can't open display: localhost:0.0

i tried to set my hostname, ipaddress and same errors.

i have to launch a xwindows application requires gui enabled environment.

i was surprised, a desktop itself should support xwindows.. why am i getting this error

any idea

thx
AK

---

### Post by taurus on 2007-05-18
How did you log in as root?

```
root@Abimanyu:~#
```

---

### Post by ak_saravanan on 2007-05-19
i used 
su -

and supplied root password

does that matter?

---

### Post by ak_saravanan on 2007-05-19
now my xclock is displaying correctly

if i do xclock from my user session it works fine

thanks for the tip

AK

---

