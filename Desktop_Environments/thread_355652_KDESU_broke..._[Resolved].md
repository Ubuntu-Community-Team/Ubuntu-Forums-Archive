---
title: "KDESU broke... [Resolved]"
date: 2007-02-07
forum: Desktop Environments
---

### Post by garethppls on 2007-02-07
[QUOTE=Konsole]
gareth@gareth-desktop:~$ kdesu kate
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
kdesu: WARNING: Daemon not safe (not sgid), not using it.
[/QUOTE]

Anyone have an idea what this means.
[B]
Found Problem, wrong chmod on /etc/sudoers, thanks anyway guys :)[/B]

---

### Post by StarsAndBars14 on 2007-02-19
I also had that problem but I had the right chmod on sudoers.

It was solved in my case by switching kdesud back to root:nogroup (I had it as root:root) then using konqueror via kdesu, going to the /usr/bin directory and switching "Advanced Permissions" on kdesud to "Set GID."

Something broke when I switched it out of "nogroup."

---

