---
title: "permisions problem! HELP!"
date: 2009-01-12
forum: General Help
---

### Post by Mercedes300 on 2009-01-12
Hi,

I'm having trouble with my Documents directory. I created a new group on my system called family, and added the users in my family to it in /etc/group.
```
family:x:15000:lastm,carol,rivertam,john
```
Logged in as carol, I chowned it with,
```
chown carol:15000 Document
```
I then chmoded it with:
```
chmod 660 documents
```
now, I can't cd to the directory! it says:
```
-bash: cd: Documents/: Permission denied
```
even if I'm root!

Pleas Help!

Thanks.

---

### Post by taurus on 2009-01-12
You need the executable permission if you want to change to that directory.

```
chmod 770 documents
```

---

### Post by Mercedes300 on 2009-01-12
Thanks! Why do you need to execute a directory?

---

