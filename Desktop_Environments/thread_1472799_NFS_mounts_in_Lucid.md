---
title: "NFS mounts in Lucid"
date: 2010-05-04
forum: Desktop Environments
---

### Post by BarryDocks on 2010-05-04
Hi, I have upgraded to Ubuntu 10.04.  Only problem mounting existing NFSv3 shares.
```
root@adrian-laptop:~# mount 10.10.64.1:/media/raid0 /media/nfs -v 
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Tue May  4 21:31:55 2010
mount.nfs: text-based options: 'addr=10.10.64.1'
mount.nfs: mount(2): Operation not supported
mount.nfs: mount to NFS server '10.10.64.1:/media/raid0' failed: RPC Error: Program not registered

```
Thanks

---

### Post by BarryDocks on 2010-05-07
Stupidly I had the wrong IP address listed for portmap in hosts.allow on the server:-(

---

