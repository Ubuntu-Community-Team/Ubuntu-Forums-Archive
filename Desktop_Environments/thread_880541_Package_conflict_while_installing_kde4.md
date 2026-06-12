---
title: "Package conflict while installing kde4"
date: 2008-08-05
forum: Desktop Environments
---

### Post by Azgu on 2008-08-05
I tried to install kde4 in my Ubuntu 8.04 and received Broken packages error for 17 different packages. I followed the thread of unmet dependencies down, and found that a package called libpq5 would not install because it had an unmet dependency with libldap2. 

Apt says that this package is no longer installable but is replaced by slapd and libldap-2.4-2. Installing these, however, did not remove the error while trying to install libpq5. 

Apt-cache show says that libpq5 doesn't even depend on libldap2, but on libldap-2.4-2.

A friend of mine (with the same release and apt-repositories) successfully installed kde4 with libldap-2.4-2 instead of libldap2, so why doesn't it work with me?

---

### Post by Azgu on 2008-08-05
I was able to get around this by installing an older version of the package through my browser (got it from here: [http://packages.ubuntu.com/gutsy/libs/libpq5](http://packages.ubuntu.com/gutsy/libs/libpq5)). Still interested in why this doesn't work with apt though.

---

