---
title: "How-to uninstall older  fglrx drivers"
date: 2012-04-15
forum: Desktop Environments
---

### Post by Azyx on 2012-04-15
Hey.
I wounder how I uninstall older fglrx-drivers on Xubuntu 11.10 64bit? 

```
[Error]A previous installation of fglrx driver detected to be loaded.
User must uninstall existing fglrx driver 
or run install with force option. 
Forcing the installation is not recommended.
```

Find how after little searching  I find his command:

```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```

Seems to work and Castalyst 12.3 install.

/Cheers

---

