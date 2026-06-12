---
title: "Sharing files between 2 Kubuntu computers."
date: 2006-09-19
forum: Desktop Environments
---

### Post by titancomputing on 2006-09-19
I've got two computers on the same network that need to share files between one another. Actually, they need to share entire hard drives between one another. Is there a way I can do like I would with windows and share a drive so that it's viewable through the network? Also, how would one be able to not share one particular private folder on the drive?

---

### Post by kick6 on 2006-09-19
samba file sharing should work.  You can then share with a windows box if need be.  I know this is just a bread crumb, but it should at least point you in the right direection.

---

### Post by mssever on 2006-09-19
Look into NFS. This is the *nix way of sharing. You can simply set the appropriate permissions on the private directory, and no one will be able to access it. Samba doesn't (easily) support this kind of permissions AFAIK.

Install NFS from Synaptic.

On the server, edit /etc/exports. Read man exports for documentation.

On the client, put something like the followinf in /etc/fstab (the IP address is the IP of the server--ideally, it should be a static IP):
```
192.168.1.50:/path/to/exported/folder      /local/mountPoint   nfs     rw,hard,intr    0 0
```

---

