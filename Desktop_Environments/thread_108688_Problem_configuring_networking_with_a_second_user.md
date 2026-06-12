---
title: "Problem configuring networking with a second user"
date: 2005-12-26
forum: Desktop Environments
---

### Post by Dearhell on 2005-12-26
I have two users, I configure well the network through system->administration->networking on the first one user

But then, I tried to do the same with my second user in other session, but the setup window that should appear going again trough system->administration->networking simply don't appear

Any idea?

Anticipate thanks

---

### Post by sciurus on 2005-12-26
Is the second user a member of the admin group? Why do you need to configure networking again; I don't believe it's a per-user setting.

---

### Post by Dearhell on 2005-12-26
I have internet without any configuration, but what I want is to get into other window machine of my network, and I need to configure certain things in order to do that

The two users are independent (there is no admin group I think), the first user was added in the installation process and the second user was added after Ubuntu installation on system->administration->user and groups

But beside this, the strange thing is that with one user I can access to system->administration->networking and with the other I can't

---

### Post by sciurus on 2005-12-26
What things do you need to configure? Does going to places-'connect to server' not work?

The admin group defines who can use sudo. The user created during install is a member of this group. Users created later aren't by default, I believe. If your second user wasn't in admin, that would explain not being able to launch networking, or anything else that requires root privileges. From system-administration-'users and groups'-properties-'user priviliges' you can change whether or not a user can execute system administration tasks.

---

### Post by Dearhell on 2005-12-26
> What things do you need to configure? Does going to places-'connect to server' not work?

Places->'connect to server' it doesn't work, it appears a window with this message:

```
'You must log in to access 192.168.200.1'
User
Dominion
Password
```

But '192.168.200.1' it's the IP of the Ubuntu Machine, and I want to access to a windows machine that has another internal IP

And you were right about users, I couldn't access to networking configuration options because of that second user permission, thx

---

### Post by sciurus on 2005-12-27
Are you sure you're inputting the right values?

Have you tried using smbfs (smbmount)?

---

