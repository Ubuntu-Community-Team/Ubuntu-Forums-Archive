---
title: "startup program"
date: 2006-05-07
forum: Desktop Environments
---

### Post by azray on 2006-05-07
How does one modify the start up program? I need to fix Firestarter by setting nopasswd.

---

### Post by Omnios on 2006-05-07
Firestarter faq page with how to set up on start up.
[http://www.fs-security.com/docs/faq.php]("http://www.fs-security.com/docs/faq.php")

```
your /etc/sudoers file in your favorite text editor and add the following line at the end:
username ALL= NOPASSWD: /usr/bin/firestarter 
Note: Debian users should replace /usr/bin/firestarter with /usr/sbin/firestarter in the above line

```

---

### Post by azray on 2006-05-07
many thanks

---

