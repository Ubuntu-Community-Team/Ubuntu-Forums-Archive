---
title: "connect to NAS via nfs"
date: 2005-12-29
forum: Desktop Environments
---

### Post by etien on 2005-12-29
Hi there,

I have a NAS at home, in the form of a PC running NASLite+ ([http://www.serverelements.com)](http://www.serverelements.com)). In short, NASlite is a featherweight linux OS running from, in my case, a usb stick. Three hard drives in the nas, named Disk-1, Disk-2, Disk-3.

I had no problem accessing the files on the nas from my mac, using the "connect to server" dialogue window, entering the following address:
"nfs://IP.of.my.nas/export/disk-1"

I have tried most tutorials available on the forum, installed all recommended packages (and more probably), checked portmap is running, checked versions of kernels and stuff, have created the /mnt/nfs mount point, but on entering the mount command I either get a "Permission denied" or the "mount:RPC program is not registered" error message.

Permissions on NASlite are non existant (they are, but by default R/W to everyone and unchangeable).

Any help much appreciated.

---

### Post by djnapster on 2008-06-27
> **etien said:**
> Hi there,

I have a NAS at home, in the form of a PC running NASLite+ ([http://www.serverelements.com)](http://www.serverelements.com)). In short, NASlite is a featherweight linux OS running from, in my case, a usb stick. Three hard drives in the nas, named Disk-1, Disk-2, Disk-3.

I had no problem accessing the files on the nas from my mac, using the "connect to server" dialogue window, entering the following address:
"nfs://IP.of.my.nas/export/disk-1"

I have tried most tutorials available on the forum, installed all recommended packages (and more probably), checked portmap is running, checked versions of kernels and stuff, have created the /mnt/nfs mount point, but on entering the mount command I either get a "Permission denied" or the "mount:RPC program is not registered" error message.

Permissions on NASlite are non existant (they are, but by default R/W to everyone and unchangeable).

Any help much appreciated.


I've got exactly the same problem :-s
Coudl some1 help me?

---

