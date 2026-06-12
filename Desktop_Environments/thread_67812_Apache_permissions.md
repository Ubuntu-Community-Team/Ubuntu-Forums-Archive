---
title: "Apache permissions"
date: 2005-09-21
forum: Desktop Environments
---

### Post by kook44 on 2005-09-21
Hi-
I have two questions about apache:

1) Who (which user) is running apache httpd (and most other daemons for that matter)?  Meaning - If I boot up a box running apache and never log in, it will serve up http requests just fine.  But the apache process has to have permission to read, and write to (via a module like php or cgi) the filesystem.     How is this regulated?

2) When I create a new file, it's default permissions are 754.  Requesting that page will yield a 403 forbidden.  Only after I chmod to 755 will apache serve the page.  Why must I add execute permissions to a file before it can be served?

---

### Post by heimo on 2005-09-21
```
grep ^User /etc/apache2/apache2.conf
``` 
probably tells you: www-data

In this case, www-data needs to have read permission to file - it does not need execute bit set. (just tried with 400 permissions). For directories, execute bit is needed - nothing else - not even read bit. (just tried it with directory permissions set to 100). Please post more information and we'll see why our experiences differ.

---

