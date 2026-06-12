---
title: "Quick Apache2 VirtualHost question"
date: 2009-04-23
forum: General Help
---

### Post by autogun on 2009-04-23
Howdy all,

I have a VirtualHosts configured in my httpd.conf file.
```
NameVirtualHost MY_IP_ADDRESS

<VirtualHost MY_IP_ADDRESS>
ServerName subdomain.domain.com
DocumentRoot /path/to/phpmyadmin
</VirtualHost>

```

So every time I browse to 'subdomain.domain.com' it points me to /path/to/phpmyadmin

How can I configure Apache so each time i come directly to the MY_IP_ADDRESS it will point me to Apache's DefaultRoot and not to the VirtualHost?

---

### Post by autogun on 2009-04-23
Bump

---

### Post by autogun on 2009-04-24
Anyone? :(

---

