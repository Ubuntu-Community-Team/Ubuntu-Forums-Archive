---
title: "powernowd starts with the wrong settings at boot"
date: 2012-06-04
forum: Desktop Environments
---

### Post by glennr on 2012-06-04
I have set up powernowd differently from the default so that the CPU is at the lowest clock speed when the load is low and at the highest whenever it does anything. After changing /etc/default/powernowd and restarting with "service powernowd restart" it works as expected, but after a reboot it uses the original settings and I need to do a "service powernowd restart" to make it use the settings in /etc/default.

How do I make it use the /etc/default settings at boot?

This is with Kubuntu 10.04.
```
$ uname -a
Linux cs 2.6.32-41-generic #89-Ubuntu SMP Fri Apr 27 22:18:56 UTC 2012 x86_64 GNU/Linux

```

---

