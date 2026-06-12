---
title: "parallel port dead"
date: 2008-12-10
forum: General Help
---

### Post by CEB2nd on 2008-12-10
Help!  The parallel port will no longer work under Hardy, my parallel port printer and scanner work fine with windows.  I have tried my parallel port  printer and scanner that used to work in Hardy but no luck, the parallel port no longer works.  I checked my computer bios and it is still set for EPP.  My computer is a duel boot windows/Hardy system. Does anyone know how to fix this?  Thanks in advance!:confused:

---

### Post by CEB2nd on 2008-12-10
Bump

Can anyone help fix this problem?

---

### Post by iponeverything on 2008-12-10
do:

```
sudo modprobe parport_serial
```

if that solves your problem then do this to make it permanent:

```
sudo echo parport_serial >> /etc/modules 
```

---

