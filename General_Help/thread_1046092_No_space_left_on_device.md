---
title: "No space left on device"
date: 2009-01-21
forum: General Help
---

### Post by kurt2000 on 2009-01-21
Hi i recieve a 28 No space left on device when trying to update :

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
  Write error - write (28 No space left on device)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
  Write error - write (28 No space left on device)
Fetched 5798kB in 12s (467kB/s)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2)  Write error - write (28 No space left on device)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2)  Write error - write (28 No space left on device)

E: Some index files failed to download, they have been ignored, or old ones used instead.

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7,4G  2,8G  4,3G  40% /
tmpfs                 1,7G     0  1,7G   0% /lib/init/rw
varrun                1,7G  384K  1,7G   1% /var/run
varlock               1,7G     0  1,7G   0% /var/lock
udev                  1,7G  2,7M  1,7G   1% /dev
tmpfs                 1,7G     0  1,7G   0% /dev/shm
lrm                   1,7G  2,0M  1,7G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6             176M  168M  8,2M  96% /var/lib

df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1             489600  146490  343110   30% /
tmpfs                 220447       4  220443    1% /lib/init/rw
varrun                220447      81  220366    1% /var/run
varlock               220447       2  220445    1% /var/lock
udev                  220447    4995  215452    3% /dev
tmpfs                 220447       1  220446    1% /dev/shm
lrm                   220447      17  220430    1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6              39440    5252   34188   14% /var/lib


This is a freshly installed mythbuntu 8.10 on a 8GB compact flash card.

What's wrong here ?

Wkr.
Svend

---

### Post by mcduck on 2009-01-21
If nothing else, your /var/lib seems to be rather small, and 96% full..

```
/dev/sda6 176M 168M 8,2M 96% /var/lib
```
There's only 8MB of space left on /dev/sda6. If the update needs to write anything to /var/lib it could easily be that 8MB is not enough.

I'm not sure if Mythbuntu requires separate partition for /var/lib for some strange reason, but if it doesn't I recommend doing a new install, this time keeping everything on one partition (since that allows most efficient disk space usage on small disks).

---

### Post by kurt2000 on 2009-01-21
Thanks, i overlooked that one.

I wonder why the installe chose that size.

Wkr.
Svend

---

### Post by hyper_ch on 2009-01-21
the installer didn't... you did :)

---

