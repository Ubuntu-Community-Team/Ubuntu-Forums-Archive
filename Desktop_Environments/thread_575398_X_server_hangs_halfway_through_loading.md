---
title: "X server hangs halfway through loading"
date: 2007-10-14
forum: Desktop Environments
---

### Post by jamadagni on 2007-10-14
This morning I shut down my system and a few minutes ago I restarted it. The shutdown was normal. But now while restarting the X server hangs halfway through the process of KDM loading. (I am using Kubuntu Gutsy RC.) I am writing this from a terminal using Lynx. Please tell me what to check to fix this problem. I have tried deleting the .Xauthority, the .ICEauthority files etc, but no use. All the X server shows me is the X symbol on a black background. Please help me to solve this problem.

---

### Post by jamadagni on 2007-10-14
I am using Kubuntu Gutsy RC. My ~/.xsession-errors file contains:
> Xsession: X session started for samjnaa at Sun Oct 14 11:25:25 IST 2007
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPClient::attachInternal. Attach failed Could not open network socket
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kdeinit: Fatal IO error: client killed
klauncher: Exiting on signal 15
kded: Fatal IO error: client killed
X connection to :0.0 broken (explicit kill or server shutdown).
That connection broken at the end was probably me shutting down the computer from the terminal. The problem seems to be at:
> DCOPClient::attachInternal. Attach failed Could not open network socket
Why this happens I don't know. Before my shutdown this morning everything was normal -- I had not upgraded any critical packages. Heck there *were* no upgrades this morning. So what happened? :confused:

---

