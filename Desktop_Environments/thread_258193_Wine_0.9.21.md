---
title: "Wine 0.9.21"
date: 2006-09-15
forum: Desktop Environments
---

### Post by eightysix on 2006-09-15
I just upgraded to the newest version of WINE through the repositories and seems to be broken. I also tried building from the source, but I'm still getting the same error.

```
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  144 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x262
  Serial number of failed request:  19
  Current serial number in output stream:  19

```

---

### Post by kennyz on 2006-09-19
I am having the exact same problem, but on a Slackware 10.2 system with NVidia driver 8774 and Wine 0.9.21.

I applied patches suggested by people on the wine-devel list, but this did not help.

The previous version of Wine, 0.9.20, works fine.

What is the version of the NVidia driver that you are using?

---

