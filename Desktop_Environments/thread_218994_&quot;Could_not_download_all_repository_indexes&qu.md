---
title: "&quot;Could not download all repository indexes&quot;"
date: 2006-07-19
forum: Desktop Environments
---

### Post by MontyV on 2006-07-19
I am getting that message when checking for updates.  I am suppose to ignore this or how do I fix?  These are the indexes.

[http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz:) 404 Not Found

- Monty

---

### Post by aysiu on 2006-07-19
The repository has changed. It's no longer ```
http://packages.freecontrib.org/ubuntu/plf/
``` It's now ```
http://packages.freecontrib.org/plf/
```

---

### Post by MontyV on 2006-07-19
> **aysiu said:**
> The repository has changed. It's no longer ```
http://packages.freecontrib.org/ubuntu/plf/
``` It's now ```
http://packages.freecontrib.org/plf/
```

So how do I change this considering all I am doing is checking for updates and it does it automatically.  Where do I go to tell ubuntu to check for this instead?

---

### Post by aysiu on 2006-07-19
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
sudo nano /etc/apt/sources.list
``` Find all lines that refer to freecontrib.org and just delete the */ubuntu* part before *plf*. Leave the rest of each line alone, though (both the parts before and after the web address. Then save (Control-X, Y, Enter) and ```
sudo aptitude update
```

---

### Post by asplode on 2006-07-19
I think someone might should stick this temporarily, I've seen about 10 threads about this in the last few days.  Darn webmasters 404'in everything.

---

