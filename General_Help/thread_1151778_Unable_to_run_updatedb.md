---
title: "Unable to run updatedb"
date: 2009-05-07
forum: General Help
---

### Post by satimis on 2009-05-07
Hi folks,

Ubuntu 8.10

# updatedb```

updatedb: fatal error: load_file: Could not open file: /etc/updatedb.conf: No such file or directory

```

# find / -name updatedb.conf
No printout.

Where can I find a copy of updatedb.conf

TIA

B.R.
satimis

---

### Post by slakkie on 2009-05-07
This is mine:


```

cat /etc/updatedb.conf
PRUNE_BIND_MOUNTS="yes"
PRUNEPATHS="/tmp /var/spool /media"
PRUNEFS="NFS nfs nfs4 afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf rpc_pipefs

```

I'm running 8.04.2

---

