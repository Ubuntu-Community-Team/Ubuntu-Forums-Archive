---
title: "eCryptfs seems to have a problem"
date: 2010-11-10
forum: Desktop Environments
---

### Post by surfer on 2010-11-10
i use ubuntu 10.10 with an eCryptfs encrypted home directory. recently i checked the syslog and saw this warning, repeated every second:

```
Nov 10 15:06:00 abcd kernel: [ 4112.975570] Valid eCryptfs headers not found in file header region or xattr region
Nov 10 15:06:00 abcd kernel: [ 4112.975582] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
```

what could this mean? and how can i get rid of it; it certainly does not look as if everything is ok...

---

### Post by surfer on 2010-11-22
ok, the problem disappeared after a reboot...

---

