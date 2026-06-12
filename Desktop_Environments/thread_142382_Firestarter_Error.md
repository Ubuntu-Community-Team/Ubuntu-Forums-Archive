---
title: "Firestarter Error"
date: 2006-03-10
forum: Desktop Environments
---

### Post by OffHand on 2006-03-10
I installed Firestarter again. 
When I tried to start it it gave me this error:

A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close.

The internet connection on my other compu stopped working too.
Re-install didn't help.
I'm a bit clueless atm.

---

### Post by cwaldbieser on 2006-03-11
[QUOTE=subsonic_shadow]I installed Firestarter again. 
When I tried to start it it gave me this error:

A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close.

The internet connection on my other compu stopped working too.
Re-install didn't help.
I'm a bit clueless atm.[/QUOTE]

Does 
```

$ sudo dkpg-reconfigure firestarter

```
help?

---

