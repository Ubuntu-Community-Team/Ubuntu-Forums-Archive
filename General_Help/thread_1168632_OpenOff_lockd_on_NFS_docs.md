---
title: "OpenOff lockd on NFS docs"
date: 2009-05-24
forum: General Help
---

### Post by gammb on 2009-05-24
FunPlugged my DLink DNS321 NAS to support NFS and changed my /etc/fstab mount from CIFS to NFS.
```
#//dlink/Volume_1	/nas	cifs	rw,soft,credentials=/root/.credbaloo 0 0
dlink:/mnt/HD_a2	/nas	nfs	rw,soft
```
Now when I use OpenOffice on any file located on the NAS, the app hangs and keeps writing to syslog
```
mydesk kernel: [ 6041.424026] lockd: server dlink not responding, still trying
```
every few seconds until I force-kill the app.

Anyone run into this before ?
TIAFAA

---

