---
title: "How to install the Goban Screensaver?"
date: 2006-05-20
forum: Desktop Environments
---

### Post by chipsdeluxe on 2006-05-20
I'd like to use the Goban screensaver, but I'm not sure how to install it.

The [Goban Screensaver]("http://draves.org/goban/") website has an RPM, SRPM, and source tarball, but I don't which to use or how. Can anyone help?

Thanks!

---

### Post by Ramses de Norre on 2006-05-20
```
sudo aptitude install alien
``` download the .rpm
```
sudo alien package.rpm
``` this will create a .deb file which you can install with:
```
sudo dpkg -i package.deb
```

---

