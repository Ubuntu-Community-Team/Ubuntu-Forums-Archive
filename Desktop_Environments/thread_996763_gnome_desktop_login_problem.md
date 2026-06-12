---
title: "gnome desktop login problem"
date: 2008-11-29
forum: Desktop Environments
---

### Post by ivearnedit on 2008-11-29
I just installed Ubuntu and the gnome desktop won't let me log in, I have to log in to gnome fail-safe to get in. Anyone come across this before. Thanks

---

### Post by __Ryan__ on 2008-11-29
You probably need to reset your password. Log into the recovery console and it will drop you into the root account.

Change your user password:

```
# passwd <username>
```

You should now be able to log into your account correctly.

---

