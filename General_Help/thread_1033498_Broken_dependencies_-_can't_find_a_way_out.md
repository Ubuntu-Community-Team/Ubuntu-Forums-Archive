---
title: "Broken dependencies - can't find a way out"
date: 2009-01-07
forum: General Help
---

### Post by Sol1 on 2009-01-07
Gurus,

I committed a cardinal sin and ran a few commands without fully understanding what they did in an attempt to change some AWN stuff.  It's completely hosed my package management.  I'm getting the following when trying to run apt-get -f install: 

```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libawn0 python-awn
The following NEW packages will be installed:
  libawn0 python-awn
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
8 not fully installed or removed.
Need to get 0B/89.2kB of archives.
After this operation, 393kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 179786 files and directories currently installed.)
Unpacking libawn0 (from .../libawn0_0.2.6-7ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn0_0.2.6-7ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-bzr
Unpacking python-awn (from .../python-awn_0.2.6-7ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python-awn_0.2.6-7ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.5/site-packages/awn/awn.so', which is also in package python-libawn-bzr
Errors were encountered while processing:
 /var/cache/apt/archives/libawn0_0.2.6-7ubuntu1_i386.deb
 /var/cache/apt/archives/python-awn_0.2.6-7ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help is very much appreciated.  I've tried fixing the packages with Synaptic with the same error.

---

### Post by namdung on 2009-01-07
```
sudo dpkg --configure -a
```

In *Synaptic Package Manager==>Custom Filter==>Broken* remove the broken packages.

Try removing awn.

---

### Post by Sol1 on 2009-01-07
Thanks for the help, Namdung.

I used Synaptic to locate broken packages and completely remove them.  I still get the following errors:

```
E: /var/cache/apt/archives/libawn0_0.2.6-7ubuntu1_i386.deb: trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-bzr
E: /var/cache/apt/archives/python-awn_0.2.6-7ubuntu1_i386.deb: trying to overwrite `/usr/lib/python2.5/site-packages/awn/awn.so', which is also in package python-libawn-bzr

```

---

### Post by Sol1 on 2009-01-07
Got this fixed by searching for "awn" and "avant" and deleting everything I found (except for the avant fonts, but those were obvious that they weren't awn related).  I was then able to reinstall.  Thanks!

---

### Post by dcstar on 2009-01-07
> **Sol1 said:**
> Got this fixed by searching for "awn" and "avant" and deleting everything I found (except for the avant fonts, but those were obvious that they weren't awn related).  I was then able to reinstall.  Thanks!

Then please mark this thread appropriately.

---

