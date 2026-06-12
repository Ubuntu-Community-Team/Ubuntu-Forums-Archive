---
title: "Running an application from bash gives Xserver errors"
date: 2007-02-18
forum: Desktop Environments
---

### Post by yurukov on 2007-02-18
Here is what I get when I run any application that has anything to do with the xserver:

```
yurukov@yurukov-laptop:~$ kwrite
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

I could not find an "input device 168" in xorg.conf, so I assume that 168 is the error code or something. Any Idea how to fix that?

---

