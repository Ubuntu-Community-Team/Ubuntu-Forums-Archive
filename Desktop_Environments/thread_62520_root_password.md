---
title: "root password"
date: 2005-09-05
forum: Desktop Environments
---

### Post by robin_egenes on 2005-09-05
I installed ubuntu and don't remember specifying a password for root; so I can't use su to change the time - the battery is obviously flat

---

### Post by evilghost on 2005-09-05
```

sudo su

```

When prompted for your password, enter the one you chose during installation.

---

### Post by robin_egenes on 2005-09-05
will do. Thanks evilqhost

---

### Post by nozey on 2005-09-05
If u dont want to use sudo, and really want to work as root ... first u need change the root password with:

```
sudo passwd root
```

---

