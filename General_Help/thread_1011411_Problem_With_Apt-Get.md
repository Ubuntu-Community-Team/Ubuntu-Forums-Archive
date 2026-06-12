---
title: "Problem With Apt-Get"
date: 2008-12-14
forum: General Help
---

### Post by computerwiz3491 on 2008-12-14
I can't seem to install anything all of a sudden. When I run apt-get upgrade I get 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-backports-modules-2.6.22-14-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 6119kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 129223 files and directories currently installed.)
Removing linux-backports-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-backports-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.22-14-generic
E: Directory '/var/log/apt/' missing
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And I get similar errors when trying anything with apt-get. Any suggestions?

---

