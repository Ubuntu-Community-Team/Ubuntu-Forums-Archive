---
title: "Updating kernel with PXE-boot clients"
date: 2012-07-09
forum: Desktop Environments
---

### Post by redxine on 2012-07-09
I followed the guide on the wiki for setting up PXE boot with ubuntu, and have two thin clients loading up xubuntu from over the network with great results.  However, I applied some updates from the update manager, including a new kernel version, and get this error whenever I use apt-get or dpkg:

```
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.26.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up numlockx (1.2-2) ...
Errors were encountered while processing:
 linux-image-3.2.0-26-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Of course since the kernel is hosted on the server I know I'll probably have to do the update and dpkg configuration on there, but I'm not sure what the correct way to go about this is.  Any help would be appreciated.

---

