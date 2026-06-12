---
title: "about finding absolute pathname"
date: 2009-02-19
forum: General Help
---

### Post by veda87 on 2009-02-19
I am using ext2 file system on linux-2.6.26. i want to know whether the file system keeps a record of the absolute pathname for each and every file that have been created. if so, where could i find it.

---

### Post by CKDewey on 2009-02-20
Have a look at the 'locate' command; you can update its database using the 'sudo updatedb' command (that process can be automated).

Here is an example of searching the dB:

```
[tom@localhost ~]$ locate rc.local
/etc/rc.local
/etc/rc.d/rc.local
[tom@localhost ~]$ 
```

---

