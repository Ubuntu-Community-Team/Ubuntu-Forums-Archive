---
title: "broken sudo - cascading errors"
date: 2007-09-16
forum: Desktop Environments
---

### Post by Blue Shift on 2007-09-16
I'm new to K/Ubuntu, and I'm trying to fix my screen resolution...  I've managed to track down the right settings for the config file, but I don't have privelages to edit it.  Of course.

In any case, I tried typing in "sudo kate", followed by my password, only to see my Konsole screen fill up with immense lists of errors.  Does anyone have any ideas as to what's gone wrong?

---

### Post by Bachstelze on 2007-09-16
Never, ever do *sudo kate*. Use *kdesu kate* instead.

---

### Post by Blue Shift on 2007-09-16
Thanks, but now I'm recieving only a few less errors.

Here, perhaps this will help:

phillip@ubuntu:~$ kdesu kate
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kio (KSycoca): ERROR: No database available!
Invalid entry (missing '=') at /tmp/kde-root/kconf_updateAUWRQa.tmp:1

---

### Post by Blue Shift on 2007-09-17
Problem solved, thanks for the help!

---

