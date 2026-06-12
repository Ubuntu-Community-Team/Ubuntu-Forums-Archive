---
title: "Change user password"
date: 2009-02-23
forum: General Help
---

### Post by Embun_pagi on 2009-02-23
I accidentally create user with useradd command without a password, now the username is useless since we don't know the password. What should I do to reset existing user password?
thanks

---

### Post by marshall.robert on 2009-02-23
System -> Administration -> Users and Groups.

Alternatively

```
sudo passwd <user>
```

---

### Post by Embun_pagi on 2009-02-23
It works. Thanks Marshall.robert

---

### Post by marshall.robert on 2009-02-23
No problem :)

---

### Post by geirha on 2009-02-23
The preferred way to create users from the CLI, is to use adduser (easy to confuse with useradd, I know). Adduser will create the user and also prompt for a password for the new user. I suspect that what you meant when you said you accidentally created a user with useradd, was that you meant to add it with adduser, but I just mention it just in case ...

---

### Post by Embun_pagi on 2009-02-23
> **geirha said:**
> The preferred way to create users from the CLI, is to use adduser (easy to confuse with useradd, I know). Adduser will create the user and also prompt for a password for the new user. I suspect that what you meant when you said you accidentally created a user with useradd, was that you meant to add it with adduser, but I just mention it just in case ...

thanks for the tips

---

