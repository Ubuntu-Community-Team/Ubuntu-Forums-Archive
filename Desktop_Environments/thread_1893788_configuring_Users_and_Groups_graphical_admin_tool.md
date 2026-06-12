---
title: "configuring Users and Groups graphical admin tool"
date: 2011-12-11
forum: Desktop Environments
---

### Post by fbusse on 2011-12-11
The "Users and Groups" graphical admin tool (German version: "Systemwerkzeuge" -> "Benutzer und Gruppen", might be translation from something like "System Tools" -> "Users and Groups") restricts display of users and groups to those that are *usually relevant* for administration - however, what I'm requested to do is "unusual":

"Usually", Debian et al. have user and group IDs 1000 and above. But I have to set GID 500 and UIDs 501 and above. The "Users and Groups" graphical admin tool allows such initially setting, but afterwards no longer displays the related users and groups (which sometimes causes confusion). Is there any way to configure the users and groups displayed in the admin tool?

---

### Post by fbusse on 2012-02-02
> **fbusse said:**
> "Usually", Debian et al. have user and group IDs 1000 and above.
[http://fedoraproject.org/wiki/Features/1000SystemAccounts](http://fedoraproject.org/wiki/Features/1000SystemAccounts)

> **fbusse said:**
> But I have to set GID 500 and UIDs 501 and above.

in /etc/login.defs:

```
UID_MIN 500
GID_MIN 500
```

---

### Post by lisati on 2012-02-02
If you've solved the problem, please mark the thread solved from the "Thread tools" drop down menu.

---

