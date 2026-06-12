---
title: "Can't log into Unity with new user account V14.04"
date: 2014-11-26
forum: Desktop Environments
---

### Post by ra2323 on 2014-11-26
Hi,

I can't log into Unity with new user account, after entering the password the login page refresh.
How ever I can login using this user via the console.
The first user, which I created during the installation work fine.

This new user have write access to all file in his home directory.

What went wrong?

Thanks

---

### Post by ra2323 on 2014-12-20
I will answer myself.

At the installtion the /home directory created as 700, the directory owner was the user that was created during the installtion.

```
chmod 755 /home
```

Solve the problem.

---

