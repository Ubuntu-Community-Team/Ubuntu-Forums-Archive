---
title: "Installing muon package manager"
date: 2012-06-06
forum: Desktop Environments
---

### Post by Elmnteee on 2012-06-06
hey everyone,

I have a problem installing the muon package manager with sudo apt-get install muon.

Became back:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  muon
0 upgraded, 1 newly installed, 0 to remove and 236 not upgraded.
Need to get 0 B/128 kB of archives.
After this operation, 532 kB of additional disk space will be used.
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0:
 field name `../../../../share/doc/libreoffice-common/examples/oo-ad-ldap.xcd.sample' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

```Sorry for asking, if the solution is in the code, but I'm new to Kubuntu.

Thanks for helping :)


Edit: 
Edited the available file and added a colon. Now I get back:
```

dpkg: error: parsing file '/var/lib/dpkg/available' near line 16:
 missing package name
E: Sub-process /usr/bin/dpkg returned an error code (2)

```Okay solved. Just cleared the file with sudo dpkg --clear-avail.

---

