---
title: "QtParted error"
date: 2006-07-25
forum: Desktop Environments
---

### Post by paulserban on 2006-07-25
Hi, I am new in linux

After fresh install, I want to resize HDD with QTParted. I got this message if I am not in root:

paul@Linux-Ubuntu:~$ qtparted
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
paul@Linux-Ubuntu:~$


In root I have this one:

root@Linux-Ubuntu:~# qtparted
qtparted: cannot connect to X server
root@Linux-Ubuntu:~#

Anybody can help?
Thanks

---

### Post by NeutrinoX on 2006-07-27
Welcome! :) Hmmm, I'm almost sure it's something involving a mis-configuration with graphic tablets. Just in case, let's wait to someone else who knows what it is exactly.

---

