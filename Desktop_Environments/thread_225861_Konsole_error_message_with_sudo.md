---
title: "Konsole error message with sudo"
date: 2006-07-30
forum: Desktop Environments
---

### Post by n.arciss.us on 2006-07-30
I get this quite often:

```
sudo kate /etc/apache2/apache2.conf
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
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
ScimInputContextPlugin()
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kio_uiserver: cannot connect to X server :0.0
DCOP aborting call from 'kate-11320' to 'kio_uiserver'
ERROR: KUniqueApplication: Registering failed!
ERROR: Communication problem with kio_uiserver, it probably crashed.
QObject::disconnect: Unexpected null parameter
~ScimInputContextPlugin()

```

or variations of it. I also see it when Automatix starts. Any ideas?

---

### Post by jonnymccullagh on 2006-07-30
[http://ubuntuforums.org/showthread.php?p=1264009](http://ubuntuforums.org/showthread.php?p=1264009)

something to do with devices we do not have.

---

### Post by n.arciss.us on 2006-07-30
> **jonnymccullagh said:**
> [http://ubuntuforums.org/showthread.php?p=1264009](http://ubuntuforums.org/showthread.php?p=1264009)

something to do with devices we do not have.


Thanks! Aparently searched too specifically.

---

