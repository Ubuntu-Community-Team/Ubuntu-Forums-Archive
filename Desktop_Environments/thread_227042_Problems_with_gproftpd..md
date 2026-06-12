---
title: "Problems with gproftpd."
date: 2006-08-01
forum: Desktop Environments
---

### Post by mcman42 on 2006-08-01
Hello. I encouter a problem when using gproftpd. Every time I start it, when I click go online (by default proftpd is offline with boot) nothing happens, checking proftpd config through gproftpd gives out an error:
```
localhost - mod_delay/0.4: warning: unable to open DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory
```
So everytime I have to manually create "var/run/proftpd" and then "proftpd.delay" under it :(  Only after that the proftpd agrees to start.

I would be glad if anyone could coe up with suggestions on how to expose of this problem.

---

