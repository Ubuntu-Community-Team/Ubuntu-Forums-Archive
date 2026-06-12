---
title: "help: kicker does not run"
date: 2006-08-27
forum: Desktop Environments
---

### Post by marcostt on 2006-08-27
[Sorry about my poor english]

After a blackout I have to run fsck manually for /dev/hda3 (where kubuntu is) for UNEXPECTED INCONSISTENCY in /dev/hda3.

I have no idea, and accept all the proposals of fsck about wrong blocks, inodes deleted, etc... finally load the xverver but when kde was loaded I get the next error message: The KDE panel (kicker) can not load main panel due to a problem in installation.

Please, help: if you need more data, say me how to get it, for example, how to get the logs.

Thank in advance.

---

### Post by marcostt on 2006-08-27
When I type kicker in konsole i get:

```
marcos@marcos-desktop:~$ kicker
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
qstring_to_xtp result code -2
marcos@marcos-desktop:~$ qstring_to_xtp result code -2
```

---

