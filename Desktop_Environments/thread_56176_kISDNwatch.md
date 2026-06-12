---
title: "kISDNwatch"
date: 2005-08-11
forum: Desktop Environments
---

### Post by jstillha on 2005-08-11
Hello

Is their a person who is using kISDNwatch under kUbuntu? Have anyone debs for this purpose, because I have problems with the configure of the sources. The configure wants a libcapi20, but a libcapi20-2 is installed.

Thanks for every answer.

Greets

Joël

---

### Post by jstillha on 2005-08-14
The fastest way to get running kisdnwatch is to download the kisdnwatch rpm from
suse 9.2 (Suse 9.2 uses libcapi20-2). Now we take alien and make a deb package with this command:

sudo alien *.rpm

* = kisdnwatch package name

To running kisdnwatch we need also libpng3 (universe tree) and kdelibs4 which is included in kubuntu.

(The solution to compile the sources is that we need libcapi20-dev, but I must test it)

---

