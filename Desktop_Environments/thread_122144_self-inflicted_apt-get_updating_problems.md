---
title: "self-inflicted apt-get updating problems"
date: 2006-01-26
forum: Desktop Environments
---

### Post by rockstar on 2006-01-26
I attempted to add web sites to the sources list according to the advise I recieved from another thread.  I copied and pasted a list for files that is supposed to change the way apt-get gets programs.  then I typed, sudo apt-get update.  I got a bunch of these:

Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
  404 Not Found

and these:

Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-backports-staging/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-backports-staging/main/binary-i386/Packages.gz)  404 Not Found

And these:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports-staging/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports-staging_main_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by aysiu on 2006-01-26
Mirrormax is dead.
See the first link of my signature.

---

### Post by rockstar on 2006-01-26
How do I install .tar.gz files I download off of sourceforge.net?

---

### Post by aysiu on 2006-01-26
[QUOTE=rockstar]How do I install .tar.gz files I download off of sourceforge.net?[/QUOTE] See the bottom of the second link of my signature. Actually, read the whole thing.

---

### Post by rockstar on 2006-01-26
I read that link several times.

When I tried to install the tar.gz I got this

paul@fantastic:~$ bz2 -xvzf azureus_2-3.3.0.6_linux.tar.bz2
bash: bz2: command not found
paul@fantastic:~$ tar -xvzf azureus_2-3.3.0.6_linux.tar.bz2
tar: azureus_2-3.3.0.6_linux.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
paul@fantastic:~$

---

### Post by rockstar on 2006-01-26
It was just a corrupted archive.  I re-downloaded it and extracted it into the home directory.

---

