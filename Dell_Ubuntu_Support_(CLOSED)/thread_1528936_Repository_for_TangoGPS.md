---
title: "Repository for TangoGPS"
date: 2010-07-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kakotako on 2010-07-11
Does anyone know how to figure out which repository has TangoGPS? I am on Hardy that came installed on my Dell Mini 9. The sources.list does not have the repository that has TangoGPS in it.

```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

```

---

### Post by ugm6hr on 2010-07-12
TangoGPS is not packaged for Hardy / 8.04 - and certainly not for the lpia Mini version.

You're better off just installing 10.04 / Lucid if you need it - it is in the Lucid repository.

Otherwise, it may be possible to manually install using the source tarball - but I won't be able to help with that.

---

### Post by kakotako on 2010-07-13
Thanks. I installed gpsdrive in the meantime. It works reasonably well.

---

