---
title: "[KDE] Error message"
date: 2007-03-07
forum: Desktop Environments
---

### Post by nuovodna on 2007-03-07
i use Ubuntu edgy. i have a problem with the KDE software: when i try to open Amarok , for example, there are a message of error:

DCOPClient::attachInternal. Attach failed Could not open network socket

The complete message is:


john@john-desktop:~$ amarok
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
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
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
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/john/.DCOPserver_john-desktop__0
and start dcopserver again.
---------------------------------

WARNING: Waiting for already running klauncher to exit.
WARNING: Waiting for already running klauncher to exit.
WARNING: Another instance of klauncher is already running!
kdeinit: Communication error with launcher. Exiting!
kio (KMimeType): WARNING: KServiceType::offers : servicetype Amarok/Plugin not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype Amarok/Plugin not found
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
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

### Post by ewankho on 2007-03-08
Try running using 'kdesu amarok'
For the invalid or uninitialized input device 168 message follow instruction [here]("http://ubuntuforums.org/showthread.php?p=1264009")

---

### Post by nuovodna on 2007-03-09
Resolved...but if i want run kde apps not with root i cannot do it!!
There is an error to writing 


kbuildsycoca: WARNING: KTempFile: Error trying to create /var/tmp/kdecache-john/

---

