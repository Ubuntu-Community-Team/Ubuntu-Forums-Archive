---
title: "Installation &amp; Unistallation help"
date: 2005-08-12
forum: Desktop Environments
---

### Post by ItIsMe on 2005-08-12
Whenever I try to remove a program through synaptic or Add/Remove Programs, or if I try to install a new program through synaptic or apt-get I get a message saying;


E: ubuntu-desktop:  files list file for package `python-imaging' is missing final newline


How do I fix this?

---

### Post by heimo on 2005-08-12
I can't remember (or check) the actual filenames right now, but somewhere... possibly /var/lib/dpkg/[somedirhere]/
are files for dpkg (debian package manager, the backend for apt-get / synaptic) and some of those files (python-imaging*) is corrupted. You can try to mark python-image for complete removal (apt-get --purge remove python-image) and reinstall (apt-get install python-image) and if that doesn't help, remove python-image related files under directory mentioned above and purge-remove and reinstall again... :)

This has a potential to screw your system, but personally I've done it many times without problems.

---

