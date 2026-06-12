---
title: "Deleted /usr/bin/dpkg"
date: 2007-04-22
forum: Desktop Environments
---

### Post by mikeize on 2007-04-22
I *accidentally* deleted this dpkg file, while trying to correct a postfix installation error.  I have no idea what to do now.  Somebody help!

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

I guess I need to replace this file, but even then, I still have the problem of broken packages and locked files.

-mike

also my 'software index' is broken!

---

### Post by dfreer on 2007-04-22
Well, to fix /usr/bin/dpkg... you can download the dpkg .deb from [http://packages.ubuntu.com](http://packages.ubuntu.com)
Extract the .deb, and then extract the data.tar.gz file inside. Find usr/bin/dpkg, and then put it in /usr/bin.

---

### Post by mikeize on 2007-04-22
*edit*

I finally followed your instructions... and it WORKED!  Thank you very much!

---

