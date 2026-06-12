---
title: "Opera fails to start"
date: 2007-06-05
forum: Desktop Environments
---

### Post by paul cooke on 2007-06-05
when run from CLI, gives the following messages before seg faulting:

paulc@broken-drum:~$ opera
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault


this is Opera 9.10 in the dapper commercial on Dapper with KDE 3.5.5

---

### Post by Colonel Kilkenny on 2007-06-06
> **paul cooke said:**
> when run from CLI, gives the following messages before seg faulting:

paulc@broken-drum:~$ opera
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault


this is Opera 9.10 in the dapper commercial on Dapper with KDE 3.5.5
Download new Opera 9.21 from opera.com and everything will work.
Canonical really should upload it to their commercial repos as well...

---

### Post by paul cooke on 2007-06-06
yup, that fixed it

---

