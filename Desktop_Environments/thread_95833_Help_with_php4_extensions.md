---
title: "Help with php4 extensions"
date: 2005-11-27
forum: Desktop Environments
---

### Post by kook44 on 2005-11-27
Hi-
I am using breezy.  I removed php5 and apache2 with synaptic, and then installed apache 1.3 and the libapache-mod-php4 package.  Php 4 is working fine, but when I install extensions (mysql, domxml, xslt, gd, etc..), they do not appear enabled when I view phpinfo().  Has anyone else ran into this?

THX!

---

### Post by kook44 on 2005-11-27
ok i fixed it.
I had to add the
```
extension=xxxxx.so
```
line for each extension in my php.ini file.
Is this normal?  I don't remember having to do that when I was using apache2 on another box.  maybe I just forgot.

Also-
Usually, when you see phpinfo() output, you can see the configure command for the build.  I don't get this?  Doesn't synaptic reconfigure & compile php every time you add an extension?

---

### Post by jefurii on 2006-01-05
thanks for posting this, kook44. adding the "extension=domxml.so" worked for me too after restarting apache2.  i'm not seeing the configure command info either.

fyi, i was also able to add other useful XML/XSLT extensions:
```
extension=domxml.so
extension=xslt.so
extension=exslt.so
```

---

