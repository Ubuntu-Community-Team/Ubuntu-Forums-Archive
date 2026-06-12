---
title: "keep getting error when compilign ksmoothdock"
date: 2006-10-04
forum: Desktop Environments
---

### Post by searayman on 2006-10-04
i get this error at the end of ./configure for ksmoothdock:


checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

---

### Post by x64Jimbo on 2006-10-05
Is there a reason you opted not to go with KXDocker? It's a much more mature project, imo.
Incidentally, it's also in the repositories - no compile necessary.

---

### Post by searayman on 2006-10-05
kxdocker wont run for some reason. But anywho i got ksmooth to work, by just ignoring the error and goign on with th emake and such.

---

### Post by searayman on 2006-10-09
this is why i dont use kxdocker, because when i use kxdocker i get this error!!!

mike@mike-desktop:~$ kxdocker
KXDocker Will use Composite Extensions!
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
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout [http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources)
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
ERROR: Communication problem with kxdocker, it probably crashed.
mike@mike-desktop:~$

---

### Post by searayman on 2006-10-10
any ideas?

---

### Post by daradib on 2006-10-29
I get the same error when using kxdocker.

[HTML]cyrusjones@DARADIB:~$ kxdocker
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
ERROR: Communication problem with kxdocker, it probably crashed.[/HTML]

I really wanted to use kxdocker. Anybody know what to do.
I am using Kubuntu 64-bit Edgy.

---

