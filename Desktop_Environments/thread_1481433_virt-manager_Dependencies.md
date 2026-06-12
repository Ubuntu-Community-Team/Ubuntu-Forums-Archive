---
title: "virt-manager Dependencies"
date: 2010-05-12
forum: Desktop Environments
---

### Post by gareththered on 2010-05-12
Hi.

I had virt-manager on my laptop to control virtual machines on a remote server. I've recently reinstalled my laptop from scratch with 10.04 LTS.

When I request that 'virt-manager' is installed it attempts to install far to many packages in my opinion:-

```
The following NEW packages will be installed
  acl bridge-utils libaio1 libdevmapper-event1.02.1 libvirt-bin libvirt0
  libxen3 lvm2 python-gtk-vnc python-libvirt python-urlgrabber qemu-common
  qemu-kvm seabios vgabios virt-manager virtinst watershed
0 upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
```As you can see, it's trying to install a full virtualization system on my laptop.  I don't need that, just the console in order to manage my server.  I probably hadn't noticed this on my previous install as I had experimented with virtualization on it and had most of those dependencies installed already.

Any ideas?  Is it a bug that needs reporting, or am I missing something here?

Thanks in advance,

Gareth

---

### Post by gareththered on 2010-05-14
Just to add, and maybe as a slight bump, it's actually libvirt-bin that drags all the other dependencies in.

I'm really not interested in having VMs run on my laptop and if I did, I personally think it would be a job for VirtualBox rather than qemu.

---

