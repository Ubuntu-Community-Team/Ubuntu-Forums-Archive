---
title: "dpkg error"
date: 2006-08-07
forum: Desktop Environments
---

### Post by gandalf2041 on 2006-08-07
After 30 reboots, my filesystem forced a fsck and marked alot of bad blocks.  The subsequent reboot went OK and my system came up fine; however, one of the cross-linked files was /var/lib/dpkg/available.  Now when I run apt-get, I get the following error:

```
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1145 package `gdb':
 EOF during value of field `Maintainer' (missing final newline)
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

How do I repair this file?

---

