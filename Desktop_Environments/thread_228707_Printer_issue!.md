---
title: "Printer issue!"
date: 2006-08-03
forum: Desktop Environments
---

### Post by tigrez on 2006-08-03
I have an HP 1005 laserjet.
Every time I switch off the printer, it lose his firmware, and I must do a shell command to put it. 
The question is simple: why nobody maked a init script for this case?

In the directory /usr/share/foo2zjs/firmware there is the firmware, and as root (no sudo) the command is simple:

# cat /usr/share/foo2zjs/firmware/sihp1005.dl > /dev/usblp0

Please someone do this in next hp printer driver! :evil:

---

