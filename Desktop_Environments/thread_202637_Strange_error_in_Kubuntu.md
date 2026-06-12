---
title: "Strange error in Kubuntu"
date: 2006-06-23
forum: Desktop Environments
---

### Post by boyx on 2006-06-23
Hi,
I just installed gparted and I am getting a strange error in a console box whenever I run any application via Alt+F2 like kcontrol or kdesu konqueror. I even completely purged gparted to correct this, however the error still persists. The strangest thing is that the command still executes although the konsole box opens with this error.

Here is the error:

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

---

### Post by aysiu on 2006-06-24
It's fine. When you run certain commands with *kdesu* from the terminal, that's what happens.

---

### Post by boyx on 2006-06-24
[QUOTE=aysiu]It's fine. When you run certain commands with *kdesu* from the terminal, that's what happens.[/QUOTE]

im not running the command from the terminal, but from run command. secondly, it wasnt happening before...

---

### Post by aysiu on 2006-06-24
So a terminal just pops up even though you're not launching it from the terminal?

---

