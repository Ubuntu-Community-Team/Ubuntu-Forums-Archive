---
title: "Firefox Permissions"
date: 2009-01-04
forum: Desktop Environments
---

### Post by buster2209 on 2009-01-04
When I run firefox as a superuser (sudo su), it works fine

When I run it as a normal user, the bookmarks and the back button wont work

I assume this is just a permissions problem with the firefox folder where it is installed

Can anyone tell me where it would be and what command I have to run? :confused:

---

### Post by zika on 2009-01-04
somewhere here I've noticed solution for that:

```
sudo chown -R usname:usname ~/.mozilla
```

(disclaimer:I havent' tried it ... ;))

---

