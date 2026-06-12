---
title: "Kwin Baghira"
date: 2006-06-28
forum: Desktop Environments
---

### Post by souteneur3190 on 2006-06-28
Is there a way to install baghira on kde from source.  I say this because the one in the respitories is oudated.  I tried installing from cvs but i cant even get the first command to work.

cvs -d:pserver:anonymous@baghira.cvs.sf.net:/cvsroot/baghira login

---

### Post by aysiu on 2006-06-28
How about this? ```
wget -c http://ftp.us.debian.org/debian/pool/main/b/baghira/kwin-baghira_0.7+cvs20060507-2_i386.deb
sudo dpkg -i kwin-baghira_0.7+cvs20060507-2_i386.deb
```

---

