---
title: "Integrating Ubuntu with Active Directory Home Directories"
date: 2006-02-03
forum: Desktop Environments
---

### Post by elliot on 2006-02-03
Following these instructions:
[http://ubuntuforums.org/archive/index.php/t-91510.html](http://ubuntuforums.org/archive/index.php/t-91510.html)
I've been able to join Ubuntu machines to my Active Directory domain.  Now I would like users Home Shares (hosted on the domain controller) to be mounted on login.

In windows this is usually specified in the user properties, something like:

```
H: = \\server\user_share\username
```

Can anyone shed some light on how I would go about mounting a windows share at login, and **using the credentials supplied at login** to do it?

---

