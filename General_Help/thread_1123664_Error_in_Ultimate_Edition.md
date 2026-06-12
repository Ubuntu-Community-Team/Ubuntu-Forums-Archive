---
title: "Error in Ultimate Edition"
date: 2009-04-12
forum: General Help
---

### Post by the_ice.e on 2009-04-12
Hi.
I have an annoying problem..
I cant update "libcairo2" with add/remove.. i didnt want to remove it because i have no idea what problems will i have then.

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: GPG error: http://dl.google.com testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://apt.debianchile.org unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2C392DFEEFD17969
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 778978B00F7992B0

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680

W: Ni mogo&#269;e dobiti http://wine.budgetdedicated.com/apt/dists/intrepid/Release  

W: Ni mogo&#269;e dobiti http://packages.medibuntu.org/dists/intrepid/Release  

W: Ni mogo&#269;e dobiti http://ppa.launchpad.net/project-neon/ubuntu/dists/intrepid/Release  

W: Ni mogo&#269;e dobiti http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release  

W: Ni mogo&#269;e dobiti http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu/dists/intrepid/Release  

W: Ni mogo&#269;e dobiti http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  404 Not Found

W: Nekaterih kazal ni mogo&#269;e prenesti, zato so preklicana, ali pa so uporabljena starejša.

```
Ni mogo&#269;e dobiti = Unable to get

Nekaterih kazal ni mogo&#269;e prenesti, zato so preklicana, ali pa so uporabljena starejša = Download cancaled, unable to download or old files are already in use

Please help.. it very annoying :mad:

---

### Post by taurus on 2009-04-12
```
sudo mv /etc/apt/sources.list.d  /etc/apt/sources.list.d.bak
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by the_ice.e on 2009-04-12
that simple? :O
ty very much

---

### Post by lilbaron on 2009-04-23
thank amigo!! tenia mucho problema con eso y ahora lo he resuelto.. 
saludos desde El Salvador...:guitar:

---

### Post by Moebius28 on 2009-05-14
Thanks taurus - worked like a charm!

---

