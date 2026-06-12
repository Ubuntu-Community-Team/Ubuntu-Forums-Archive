---
title: "saned only runs as root"
date: 2009-05-24
forum: General Help
---

### Post by funkydan2 on 2009-05-24
Hi,

(In Jaunty) I'm trying to setup saned to run as a daemon to allow network scanning. However running saned the normal way (through /etc/init.d/saned) doesn't work (the daemon runs, but when I run scanimage -L from a client it reports no scanners).

However, if i run *sudo saned -a* it works as expected. The daemon runs, and clients can connect. Unfortunately if I run *sudo saned -a saned* it fails in the exact same way as if I run it through init.d

The user 'saned' is a member of the scanner group, so I don't know what else to do. Maybe it's something to do with the scanner not being owned by the 'scanner' group, but I don't know how to check that.

Daniel

PS - Running 'scanimage -L' on the server/host as a normal user reports the connected scanner.

PPS - Although I only used it once or twice, I think this scanner worked over the network under 8.10, and the error has only occured since upgrading to 9.04.

---

