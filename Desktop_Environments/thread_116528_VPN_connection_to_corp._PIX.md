---
title: "VPN connection to corp. PIX"
date: 2006-01-12
forum: Desktop Environments
---

### Post by bensode on 2006-01-12
Working on trying to establish a VPN connection to my corporate PIX from Ubuntu 5.10 and not sure where to start.  Under Windows we use the SafeNet (SoftRemote) client and there doesn't seem to be a linux client available.  I've tried using Wine, Cedega and even CXoffice installations of the Windows client but they all are failing.  Any ideas to get a VPN working?

---

### Post by hajk on 2006-01-13
You could ask the IT folks at your company whether a CISCO client could be used -- in that case installing the vpnc package is worth considering. This is what I'm using myself. 

If it's not a CISCO VPN client, then the pptp package could be the answer, although I don't have any experience with it.

Anyway, this should get you going forward a bit.

---

