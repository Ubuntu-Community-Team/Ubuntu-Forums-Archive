---
title: "removing /cdrom from apt-get?"
date: 2005-07-30
forum: Desktop Environments
---

### Post by afabco on 2005-07-30
This has got to be an FAQ, but I can't find it, so I apologize in advance.

How do I remove the /cdrom/ from the apt-get install path?  I prefer to just get all packages from network since I frequently work remote.

Thanks in advance!

---

### Post by adwait on 2005-07-30
I don't exactly remember, but just edit the /etc/apt/sources.list file using

```
sudo gedit /etc/apt/sources.list
```

Search for the CDROM entry and delete it......

---

### Post by afabco on 2005-07-30
Thanks for the fast reply!

I thought that I'd done that, and cdrom wasn't in the sources.list.

It was.

It's the very first line.

Rem'ed it out.

It worked.

Arrgh.

<bang head against table muttering 'idiot idiot'.>

Anyway thanks again!

---

### Post by adwait on 2005-07-31
Hehe......no problem :)

---

