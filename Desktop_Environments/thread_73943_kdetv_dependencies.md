---
title: "kdetv dependencies"
date: 2005-10-10
forum: Desktop Environments
---

### Post by AndreasMeier on 2005-10-10
Hi there,

I tried to get kdetv to work, but when I tried to install it, I only got several dependency errors like this:
kdetv:
  depends from: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is installed
  depends from: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is installed
  depends from: libidn11 (>=0.5.13) but 0.5.2-3 is installed
  depends from: libqt3c102-mt (>=3:3.3.4) but 3:3.3.3-7ubuntu3 is installed

Seems so, that I dont have the latest packages available.
Regarding the first dependency, the libc6, I found several more updates waiting for the new version,

so, do you have any repos for me to get that thing working :-)

Thanks in advance,

regards
Andreas

---

### Post by ranf on 2005-10-10
[QUOTE=AndreasMeier]
I tried to get kdetv to work, but when I tried to install it, I only got several dependency errors like this:
kdetv:
  depends from: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is installed
  depends from: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is installed
  depends from: libidn11 (>=0.5.13) but 0.5.2-3 is installed
  depends from: libqt3c102-mt (>=3:3.3.4) but 3:3.3.3-7ubuntu3 is installed
[/QUOTE]
Looks like this .deb is made for Debian Sarge.
In about 3 days Ubuntu 5.10 should be available.
I suppose it will work then.

---

