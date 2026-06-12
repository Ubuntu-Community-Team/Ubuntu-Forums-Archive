---
title: "apache2 has taken over my lighty install"
date: 2009-04-23
forum: General Help
---

### Post by fontenot_1031 on 2009-04-23
When I start my computer apache2 takes over on port 80 as the default web server. I can stop it with sudo /etc/init.d/apache2 stop but when I try to apt-get remove apache2 apt-get says it can't find apache2 installed. I'm wondering if another program installed apache2 partly.

Can anyone help me get back my lighttpd (and possibly get rid of apache2 forever)?

---

### Post by prem1er on 2009-04-23
Did you try to purge apache?

```
sudo apt-get remove --purge apache
```

---

### Post by fontenot_1031 on 2009-04-23
Found the package and fixed. Thank you

```
sudo apt-get remove apache2.2-common
```

Don't know how that got there.

---

