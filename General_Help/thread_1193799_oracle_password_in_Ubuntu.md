---
title: "oracle password in Ubuntu"
date: 2009-06-21
forum: General Help
---

### Post by oakdeveloper on 2009-06-21
Hi,

I have installed Oracle XE  on my Ubuntu 9.04. After the installation, I saw that a user by name 'oracle' was created. What is the password for this user ?

Regards,
Babu

---

### Post by Waappu on 2009-06-22
Hi

As I understarnd password is not set for that users and you can not login with using that user name.

But if you like use that user, you can set password. I'm not recomend that.
```
sudo passwd oracle
```

Also you can become user oracle by command```
sudo su - oracle
```

---

