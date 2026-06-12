---
title: "Snowballz won't start!"
date: 2008-02-29
forum: Gaming &amp; Leisure
---

### Post by apricot on 2008-02-29
Other games working fine, 3d acceleration enabled.

Here is the output when i do terminal: snowballz
```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x75
  Serial number of failed request:  127
  Current serial number in output stream:  129

```

---

### Post by hasufell on 2009-04-30
quite the same error-message here.

ubuntu 8.04, fglrx, other games working fine

---

### Post by gra2uitous on 2009-05-12
I had the same problem and found a bug listed on launchpad [https://bugs.launchpad.net/ubuntu/+source/snowballz/+bug/155496](https://bugs.launchpad.net/ubuntu/+source/snowballz/+bug/155496) that suggested trying to turn fullscreen mode off in the 'ini' file  ~/.snowballz.ini.   

Worked for me!!

---

