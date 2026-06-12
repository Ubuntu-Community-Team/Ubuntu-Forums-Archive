---
title: "Ubuntu 6.06.1 LTS"
date: 2006-08-14
forum: Desktop Environments
---

### Post by fragos on 2006-08-14
Just wanted to make sure that there isn't any difference between my up to date 6.06 and 6.06.1.  I would think not but since it wasn't specifically stated, one has to wonder.

---

### Post by Jagot on 2006-08-14
Providing you've done all the updates then you should have 6.06.1.  You can check by running this command in terminal:

```
lsb_release -a
```

---

### Post by ExMachina on 2006-08-14
user@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper

I did:

sudo apt-gte update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Is that output what i should ahve?

---

### Post by fragos on 2006-08-14
Jagot,

Thanks.  As an engineer I'm very literal.  I got the same output to "lsb_release -a" as ExMachina but all my updates came from the Ubuntu automated updates.

---

### Post by Jagot on 2006-08-15
Yep - that output is what you should have.  You don't need to dist-upgrade for 6.06.1 as it's not a new release as such, so automated updates will get you to the same position

---

