---
title: "Problem installing tspc / ipv6"
date: 2009-01-30
forum: General Help
---

### Post by adxvd on 2009-01-30
Hi, when I try to install tspc to get ipv6 on my ubuntu server I get an error, not sure why and was hoping someone would help :)

```
[removed]:~$ sudo apt-get install tspc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tspc is already the newest version.
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd linux-headers-2.6.24-16-generic
  linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tspc (2.1.1-6ubuntu2) ...
Setting up IPv6 tunnel: No IPv6 support found
Try "modprobe ipv6"

Error is 3: INTERFACE_SETUP_FAILED
TSP session done
invoke-rc.d: initscript tspc, action "start" failed.
dpkg: error processing tspc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tspc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks in advance :P :)

---

