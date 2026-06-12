---
title: "can not see directory even if exist"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Lualah on 2006-09-13
i click on directory in my page then i get this error

```

Object not found!
The requested URL was not found on this server. The link on the referring page seems to be wrong or outdated. Please inform the author of that page about the error. 

If you think this is a server error, please contact the webmaster. 

Error 404
calcio.mine.nu
Wed Sep 13 16:44:40 2006
Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a 

```

directory exist, if i create other directory and try to connect on it works.

Why in this not working? How can i repeare this?
thx

---

### Post by lamego on 2006-09-13
Have you checked the apache error log for a clue ?

---

### Post by Lualah on 2006-09-14
fixed, thx for advice.

---

### Post by lamego on 2006-09-14
/etc/apache2/usr/share/awstats/icon/
Are yoy trying to access to the "icon" directory ?
If yes the error message clearly explains that you have directory indexing disabled, meaning you can't browse the directory.

---

