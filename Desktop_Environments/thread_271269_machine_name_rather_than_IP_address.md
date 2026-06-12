---
title: "machine name rather than IP address"
date: 2006-10-04
forum: Desktop Environments
---

### Post by grough on 2006-10-04
I often see examples of people refering to machines on a LAN using the real machine names like this:

e.g. user@mediaserver rather than user@192.1.168.102

How can I access local machines in this way, using the names I assigned during the ubuntu install, rather than an explicit IP?

Thanks

---

### Post by bswilson on 2006-10-04
> **grough said:**
> How can I access local machines in this way, using the names I assigned during the ubuntu install, rather than an explicit IP?

Well, like you stated, Ubuntu should use the name you gave your system during setup.  But if not, you can run this command:

```
$ sudo /bin/hostname <servername>
```

Where **<servername>** is the name you want your machine to be called.

---

