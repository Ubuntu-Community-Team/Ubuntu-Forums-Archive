---
title: "CIFS VFS: Server not Responding"
date: 2008-12-14
forum: General Help
---

### Post by donnie_ on 2008-12-14
I set up fstab to mount 2 samba shares using cifs which worked Ok then I noticed at shutdown:-

CIFS VFS: Server not Responding
CIFS VFS: No Response for Cmd 50 mid 114 

      2 messages which would halt the shutdown process for about 3 mins. I removed cifs from fstab and used smbfs instead which also worked OK, The problem is that the messages and wait at shutdown still continue. The cmd and mid codes vary. 
   
ubuntu 8.04. 
I am not mounting any cifs shares.

Any help would be much appreciated,

Thanks

---

### Post by Mindzai on 2009-03-20
I get exactly the same on Ubuntu 8.10. Anyone have any idea what's going on?

EDIT:

This should fix it HOWEVER, check that the files concerned are named as below on your system (they should be by default). The basic idea is to unmount the drives (umountfs) *before* taking down the network connection (wpa-ifupdown):

```

cd /etc/rc6.d/
sudo mv S31umountnfs.sh S14umountnfs.sh
cd /etc/rc0.d/
sudo mv S31umountnfs.sh S14umountnfs.sh

```

More info here: [http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/](http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/)

---

