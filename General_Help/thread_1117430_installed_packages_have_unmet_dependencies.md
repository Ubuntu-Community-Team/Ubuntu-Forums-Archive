---
title: "installed packages have unmet dependencies?"
date: 2009-04-05
forum: General Help
---

### Post by mdgrech on 2009-04-05
Hi I have Jaunty here and I'm getting an error of unmet dependencies.  I click on the red circle on my task bar and click install updates, it attempts to install libmysqlclient15-dev and fails.  

The error message reads:

E: /var/cache/apt/archives/libmysqlclient15-dev_5.1.30really5.0.75-0ubuntu10_amd64.deb: trying to overwrite `/usr/include/mysql/mysql.h', which is also in package libmysqlclient-dev

Please help me :guitar:

---

### Post by adult swim on 2009-04-06
you may try to force the package to overwrite
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libmysqlclient15-dev_5.1.30really5.0.75-0ubuntu10_amd64.deb
```

---

