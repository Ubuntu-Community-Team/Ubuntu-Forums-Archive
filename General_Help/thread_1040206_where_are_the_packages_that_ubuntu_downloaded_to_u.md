---
title: "where are the packages that ubuntu downloaded to update my system"
date: 2009-01-15
forum: General Help
---

### Post by newbietolinux on 2009-01-15
Hi guys, I have ubuntu 8.10 installed on a machine which has an internet connection. I have downloaded multimedia codecs and other addins for that system using the ubuntu package manager. But I have to install all the packages that I installed on that system to my friends system which does not have an internet connection. Can u please tell where the package manager saved those packages that it downloaded. Thanks...

I can redownload the packages if necessary. But please suggest a graphical way to do it as I am very bad at the command line.

---

### Post by taurus on 2009-01-15
```
ls -la **/var/cache/apt/archives**
```

---

