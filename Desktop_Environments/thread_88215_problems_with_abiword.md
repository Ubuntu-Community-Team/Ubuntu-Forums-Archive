---
title: "problems with abiword"
date: 2005-11-09
forum: Desktop Environments
---

### Post by eoinmonty on 2005-11-09
Hi i am having a problem with abiword im fairly sure i never installed it yet i can not install or update anything as i keep getting this error

"The following packages have unmet dependencies:
abiword-common: Depends: abiword but it is not installed or
abiword-gnome but it is not installed
E: Unmet dependencies. Try using -f."

if i open synaptic it tells me that the abiword-common package is broken but its unable to fix it

i also am unable to uninstall abi-word common i get this error

dpkg: parse error, in file `/var/lib/dpkg/status' near line 857 package `abiword-gnome':
missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

thanks in advance!

---

### Post by daller on 2005-11-24
[QUOTE=eoinmonty]Hi i am having a problem with abiword im fairly sure i never installed it yet i can not install or update anything as i keep getting this error

"The following packages have unmet dependencies:
abiword-common: Depends: abiword but it is not installed or
abiword-gnome but it is not installed
E: Unmet dependencies. Try using -f."

if i open synaptic it tells me that the abiword-common package is broken but its unable to fix it

i also am unable to uninstall abi-word common i get this error

dpkg: parse error, in file `/var/lib/dpkg/status' near line 857 package `abiword-gnome':
missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

thanks in advance![/QUOTE]

Try running this from a console:

sudo apt-get -f install

---

