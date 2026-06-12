---
title: "Upgrading from KDE 4.1 to 4.2 Python Error"
date: 2009-02-21
forum: Desktop Environments
---

### Post by SuperNomad on 2009-02-21
I installed kde 4.1 using apt-get and then attempted to upgrade to version 4.2 by adding the experimental PPA repository and then did:

sudo apt-get update && sudo apt-get dist-upgrade.

Things were going well, everything downloaded at a good speed until it came to unpacking one of the packages, I got this error.

Unpacking replacement kdenetwork ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-kde4_4%3a4.2.0-0ubuntu1~intrepid~ppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anyone advise me on the best course of action?

Edit: Fixed it by installing the packages manually.

---

