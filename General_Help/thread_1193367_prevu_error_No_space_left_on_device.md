---
title: "prevu error: No space left on device"
date: 2009-06-21
forum: General Help
---

### Post by chandra on 2009-06-21
I am trying to compile kate from Karmic source using prevu on a Jaunty machine with lots of hard disk space on all partitions. I have confirmed that no partition is even close to maxing out. The highest usage is on my root (/) partition at 59.6% with almost 8 GB free.

The build of qt4-x11-4.5.1 proceeds successfully until almost the end when it fails with the message:
```
cp: writing `debian/libqt4-qt3support//usr/lib/libQt3Support.so.4.5.1': No space left on device
dh_install: command returned error code 256
make: *** [binary-install/libqt4-qt3support] Error 1
dpkg-buildpackage: failure: fakeroot debian/rules binary gave error exit status2
```

I have two questions:

1. Why does this error occur?

2. How can I work around it?

Many thanks.

---

