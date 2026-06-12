---
title: "add an active directory user or group to a linux group."
date: 2009-06-09
forum: Desktop Environments
---

### Post by nublaii on 2009-06-09
So... can you post an example of what the syntax of the /etc/group file is? I can't get the right syntax...

By uppercase you mean both the domain and the username?

---

### Post by Stuart42 on 2009-06-09
> **nublaii said:**
> So... can you post an example of what the syntax of the /etc/group file is? I can't get the right syntax...

By uppercase you mean both the domain and the username?

Here's a line from my /etc/group file.

cdrom:x:24:localuser,'DOMAIN\domainuser'

Domain user needs backticks, that is all.

---

### Post by nublaii on 2009-06-09
Mmm...

If I type

```
adduser domainuser admin
```

The user gets added to the admin group and it works fine

```
adduser 'DOMAIN\domainuser' admin
```

The user gets added without the backticks and it doesn't work

If I edit the /etc/group file and add the backticks, it still doesn't work...

May it has something to do with the fact that I have

```
assume-default-domain = yes
```

on the samba config?

---

