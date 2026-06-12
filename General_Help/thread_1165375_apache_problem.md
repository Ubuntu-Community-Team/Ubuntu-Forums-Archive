---
title: "apache problem"
date: 2009-05-20
forum: General Help
---

### Post by zigmo on 2009-05-20
I'm trying to get webDAV setup on my computer for a project I'm working on. I'm running kubuntu through fluxbox. I've been following the directions here:

[http://www.linux.org/docs/ldp/howto/Apache-WebDAV-LDAP-HOWTO/intro.html](http://www.linux.org/docs/ldp/howto/Apache-WebDAV-LDAP-HOWTO/intro.html)

and things were working pretty much okay. I loaded apache2 by following the directions but when I got to:

```
# /usr/local/apache2/bin/apachectl start
```

I got the following error:

```
httpd: Could not determine the server's fully qualified domain name, using 127.0.1.1 for Servername
(98) Address already in use: make_sock: could not bind to address [::]80
no listening sockets available, shutting down
Unable to open logs
```

Any help or suggestions would be appreciated.

[edit]

I found a much better tutorial here --> [http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10](http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10)

Everything seems to work fine now. I'm a little concerned about all the other junk I loaded, but it doesn't seem to be effecting the system. Next task: find out what all my running processes are and how to get rid of the ones I don't need.

---

