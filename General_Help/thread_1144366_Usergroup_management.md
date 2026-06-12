---
title: "User/group management"
date: 2009-04-30
forum: General Help
---

### Post by tenmilez on 2009-04-30
I'm wondering why these are different. 

```
christopher@morgan-server:~$ groups christopher
christopher adm dialout cdrom plugdev lpadmin sambashare admin mysql glassfish svn
christopher@morgan-server:~$ groups
christopher adm dialout cdrom plugdev lpadmin sambashare admin
```

I would think that they should be the same, is it possible I have multiple "christopher" users and I'm logged in as the wrong one?

---

### Post by tenmilez on 2009-04-30
> **tenmilez said:**
> I'm wondering why these are different. 

```
christopher@morgan-server:~$ groups christopher
christopher adm dialout cdrom plugdev lpadmin sambashare admin mysql glassfish svn
christopher@morgan-server:~$ groups
christopher adm dialout cdrom plugdev lpadmin sambashare admin
```

I would think that they should be the same, is it possible I have multiple "christopher" users and I'm logged in as the wrong one?

Seems as though that it is possible. I was logged in via ssh and the changes hadn't taken effect on the current instance of "christopher", but after logging out/in they were applied.

---

